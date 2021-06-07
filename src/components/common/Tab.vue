<template>
    <article class="tab-item" :class="{'hide-tab': !isActive}">
        <slot />
    </article>
</template>

<script>
export default {
    name: 'Tab',
    props: {
        active: Boolean
    },
    data() {
        return {
            isActive: false
        }
    },
    mounted() {
        this.isActive = this.active;
    }
}
</script>

<style lang="scss">
@include MediaQueries($desktop-and-above) {
    .tab-item {
      @include flex();
    }

}
.hide-tab {
    visibility: hidden;
    overflow-y: hidden;
    height: auto;
    max-height: 0;
    z-index: -1;
}
</style>