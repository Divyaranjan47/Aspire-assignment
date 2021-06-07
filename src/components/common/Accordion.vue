<template>
    <article class="accordion">
        <a class="accordion_header" @click="toggleAccordion">
            <span class="accordion_header_desc">
                <slot name="acc-head" />
            </span>
            <img class="accordion_header_icon" v-if="!isOpen" src="../../assets/down-arrow.svg" alt="" />
            <img class="accordion_header_icon" v-if="isOpen" src="../../assets/up-arrow.svg" alt="" />
        </a>
        <section class="accordion_content" v-if="isOpen">
            <slot name="acc-content" />
        </section>
        <section class="accordion_add" v-if="isOpen">
            <slot name="acc-add" />
        </section>
    </article>
</template>

<script>
export default {
    name: 'Accordion',
    props: {
        open: Boolean
    },
    data() {
        return  {
            isOpen: false
        }
    },
    mounted() {
        this.isOpen = this.open;
    },
    methods: {
        toggleAccordion() {
            this.isOpen = !this.isOpen;
        }
    }
}
</script>

<style lang="scss" scoped>
.accordion {
    margin: 2.4rem;
    background: $white;
    border-radius: 8px;
    filter: drop-shadow(0 2px 8px #00000014);

    &_header {
        @include flex();
        @include justify-content(space-between);
        @extend .acc-head;
        position: relative;
        padding: 2.5rem;
        background: $light-blue;
        border: 1px solid $border-grey;
        border-radius: 8px;
        z-index: $index3;

        &_desc {
           @include flex(); 
        }

        .img {
            margin: 0 1.2rem 0 0;
        }
    }

    &_content {
       position: relative;
       background: $white;
       top: -10px;
       padding: 2.5rem; 
       z-index: $index2;
       border: 1px solid $border-grey;
       border-radius: 8px;
    }

    &_add {
       position: relative;
       top: -20px;
       background: $green-btn;
       text-align: center;
       z-index: $index1;
       border: 1px solid $border-green;
       border-radius: 8px;
       padding: 2rem;
    }
}
</style>