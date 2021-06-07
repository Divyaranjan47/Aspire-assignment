<template>
  <article class="card-dot">
      <template v-if="number.isDot">
        <span class="card-dot_item"></span>
        <span class="card-dot_item"></span>
        <span class="card-dot_item"></span>
        <span class="card-dot_item"></span>
      </template>
      <template v-else>
          <span class="card-dot_value">{{number.value}}</span>
      </template>
  </article>
</template>

<script>
export default {
    name: 'CardDot',
    props: {
        number: Object
    }
}
</script>

<style lang="scss" scoped>
    .card-dot {
        @include flex();
        margin-right: 2rem;
        &_item {
            height: 0.8rem;
            width: 0.8rem;
            background: $white;
            border-radius: 50%;
            margin: 0.8rem 0.3rem;
        }

        &_value {
            padding-right: 1.01rem;
        }
    }
</style>