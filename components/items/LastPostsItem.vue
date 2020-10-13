<template>
  <article class="LastPostItem">
    <div v-if="article.private" class="LastPostItem__lock">
      <IconLockOutline width="24" />
    </div>
    <figure v-if="article.cover" class="LastPostItem__figure">
      <nuxt-link :to="{ name: 'articles-slug', params: { slug: article.slug } }">
        <img :src="article.cover.formats.thumbnail.url" :width="article.cover.formats.thumbnail.width">
      </nuxt-link>
    </figure>
    <div class="LastPostItem__info">
      <nuxt-link :to="{ name: 'articles-slug', params: { slug: article.slug } }" class="LastPostItem__title">
        {{ article.title }}
      </nuxt-link>
      <p class="LastPostItem__meta">
        <nuxt-link v-if="firstCategory" :to="{ name: 'categories-slug', params: { slug: firstCategory.slug } }" :style="`color: ${firstCategory.color}`">
          {{ firstCategory.title }}
        </nuxt-link>
        <span class="LastPostItem__ago">
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
      return this.$moment(this.article.createdAt).fromNow()
    },
    firstCategory () {
      return this.article.categories[0] || null
    }
  }
}
</script>

<style lang="scss">
  .LastPostItem {
    display: flex;
    align-items: center;
    margin-bottom: 2rem;
    position: relative;

    &:hover {
      text-decoration: none;
    }

    &__lock {
      position: absolute;
      right: 0;
      top: 0;
    }

    &__figure {
      display: inline-block;
      margin-right: 1.5rem;
      max-width: 50%;

      img {
        border-radius: 2rem;
        overflow: hidden;
      }
    }

    &__info {
      flex-grow: 1;
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
