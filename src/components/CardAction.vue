<template>
    <article class="card-action">
        <ImageText v-for="action in actions" :key="action.id" :alt="action.alt" :text="action.text" />
    </article>
</template>

<script>
import ImageText from './common/ImageText';

export default {
    name: 'CardAction',
    components: {
        ImageText
    },
    data() {
        return {
            actions: [
                {
                    id: 1,
                    alt: '',
                    text: 'Freeze card'
                },
                {
                    id: 2,
                    alt: '',
                    text: 'Set spend limit'
                },
                {
                    id: 3,
                    alt: '',
                    text: 'Add to GPay'
                },
                {
                    id: 4,
                    alt: '',
                    text: 'Replace card'
                },
                {
                    id: 5,
                    alt: '',
                    text: 'Cancel card'
                }
            ]
        }
    }
}
</script>

<style lang="scss" scoped>
.card-action {
    @include flex();
    @include justify-content(space-between);
    padding: 2rem 2.7rem;
    background: $sky-blue;
    border-radius: 16px 16px 0 0;
}
</style>