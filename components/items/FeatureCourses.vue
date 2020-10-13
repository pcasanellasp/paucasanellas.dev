<template>
  <article class="FeatureCourses">
    <figure v-if="article.cover" class="FeatureCourses__figure">
      <nuxt-link :to="{ name: 'articles-slug', params: { slug: article.slug } }">
        <img :src="article.cover.formats.thumbnail.url" :width="article.cover.formats.thumbnail.width">
      </nuxt-link>
    </figure>
    <div class="FeatureCourses__info">
      <nuxt-link :to="{ name: 'articles-slug', params: { slug: article.slug } }" class="FeatureCourses__title">
        {{ article.title }}
      </nuxt-link>
      <p class="FeatureCourses__meta">
        <nuxt-link v-if="firstCategory" :to="{ name: 'categories-slug', params: { slug: firstCategory.slug } }" :style="`color: ${firstCategory.color}`">
          {{ firstCategory.title }}
        </nuxt-link>
        <span class="FeatureCourses__ago">
          {{ fromNow }}
        </span>
      </p>
    </div>
  </article>
</template>

<script>
export default {
  props: {
    article: {
      type: Object,
      required: true
    }
  },
  computed: {
    fromNow () {
      return this.$moment(this.article.updatedAt).fromNow()
    },
    firstCategory () {
      return this.article.categories[0] || null
    }
  }
}
</script>

<style lang="scss">
  .FeatureCourses {
    position: relative;
    margin-right: 1rem;
    &__figure {
      img {
        border-radius: 1rem;
        overflow: hidden;
        width: 100%;
      }
    }

    &__info {
      position: absolute;
      bottom: 2rem;
      padding: 1rem;
      background-color: white;
      border-radius: 0.5rem;
      width: calc(100% - 2rem);
      left: 1rem;
    }

    &__title {
      font-weight: bold;
      margin-bottom: .5rem;
      color: $gray-dark;
      display: block;
    }

    &__ago {
      float: right;
      color: $gray-400;
      font-size: $small-font-size;
    }
  }
</style>
