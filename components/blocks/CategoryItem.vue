<template>
  <nuxt-link :to="{ name: 'categories-slug', params: { slug: category.slug } }" class="Category-item" :style="computedStyles">
    <p class="Category-item__title">
      {{ category.title }}
    </p>
    <div v-if="category.cover">
      {{ }}
    </div>
  </nuxt-link>
</template>

<script>
export default {
  props: {
    category: {
      type: Object,
      required: true
    }
  },
  computed: {
    computedStyles () {
      return {
        'background-color': this.category.color,
        'background-image': this.category.cover ? `url(${this.category.cover.formats.thumbnail.url})` : null
      }
    }
  }
}
</script>

<style lang="scss">
.Category-item {
  padding: 4rem 2rem;
  display: block;
  border-radius: 1rem;
  margin-bottom: 1rem;
  color: white;
  background-repeat: no-repeat;
  background-position: 95% bottom;

  &:hover {
    text-decoration: none;
  }

  &__title {
    font-size: $h5-mobile;
  }
}
</style>
