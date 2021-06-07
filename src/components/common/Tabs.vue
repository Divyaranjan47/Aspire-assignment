<template>
    <section class="tab">
        <ul class="tab_header">
            <li class="tab_header_item" v-for="(tab, i) in tabs" :key="`${tab.name}-${i}`" :class="{'active': tab.isActive}">
                <button class="tab_header_item_btn" v-html="tab.$attrs.name" @click="selectTab(tab)"></button>
            </li>    
        </ul>
        <div class="tab_content">
            <slot />
        </div>
    </section>
</template>
<script>
export default {
    name: 'Tabs',
    data() {
        return {
           tabs: []
        }
    },
    created() {
        this.tabs = this.$children;
    },
    methods: {
        selectTab(selectedTab) {
            this.tabs.forEach(tab => {
                tab.isActive = (tab.$attrs.name == selectedTab.$attrs.name);
            });
            this.$emit('tabChanged');
        }
    }
}
</script>
<style lang="scss" scoped>
.tab {
    &_header {
        @include flex();
        padding-left: 3rem;

        @include MediaQueries($tablet-and-below) {
            position: sticky;
            top: 12.5rem;
        }
        &_item {
            list-style: none;
            margin: 0 3rem .5rem 0;
            &.active {
                border-bottom: 2px solid $blue-text;
            }

            .active & {
                &_btn {
                    @extend .tab-header-active;
                    opacity: 1;
                }
            }

            &_btn {
                @extend .btn-nostyle, .tab-header;
                padding: 0;
                opacity: 0.5;
            }
        } 
    }

    &_content {
        padding: 2.5rem 0 0;
    }
}
@include MediaQueries($desktop-and-above) {
    .tab {
        &_content {
            margin: 1rem 0 1rem 3rem;
            padding: 4rem;
            filter: drop-shadow(2px 2px 6px #00000014);
            border-radius: 8px;
            background: $white;

        }
        &_header {
            &_item {
                .active &{
                    &_btn {
                        color: $black-text;
                    }
                }
                &_btn {
                    color: $black-text;
                }
            }
        }
    }
}
</style>