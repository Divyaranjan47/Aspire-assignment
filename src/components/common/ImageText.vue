<template>
  <article class="image-text">
      <img :name="text" class="image-text_img" :src="require(`../../assets/${text.toLowerCase().split(' ').join('-')}.svg`)" :alt="alt" />
      <p class="image-text_item">{{text}}</p>
  </article>
</template>

<script>
export default {
    name: 'ImageText',
    props: {
        alt: String,
        text: String
    }
}
</script>

<style lang="scss">
.image-text {
    text-align: center;
    &_item {
        @extend .pay-text;
        display: block;
        @include MediaQueries($desktop-and-above) {
            margin: 0 0.5rem;
        }
    }
}
</style>