<template>
  <button class="details-action" @click="showDetails">{{text}}</button>
</template>

<script>
export default {
    name: 'DetailsAction',
    props: {
        text: String
    },
    methods: {
        showDetails() {
            return true;
        }
    }
}
</script>

<style lang="scss">
.details-action {
    @extend .green-text;
    background: none;
    border: none;
}
</style>