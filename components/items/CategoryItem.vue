<template>
  <nuxt-link :to="{ name: 'categories-slug', params: { slug: category.slug } }" class="CategoryItem" :style="computedStyles">
    <h3 class="CategoryItem__title">
      {{ category.title }}
    </h3>
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
.CategoryItem {
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
}
</style>
