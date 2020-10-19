<template>
  <article class="FeatureCourses">
    <figure v-if="course.cover" class="FeatureCourses__figure">
      <nuxt-link :to="{ name: 'courses-slug', params: { slug: course.slug } }">
        <img :src="course.cover.formats.thumbnail.url" :width="course.cover.formats.thumbnail.width">
      </nuxt-link>
    </figure>
    <div class="FeatureCourses__info">
      <nuxt-link :to="{ name: 'courses-slug', params: { slug: course.slug } }" class="FeatureCourses__title">
        {{ course.title }}
      </nuxt-link>
      <p class="FeatureCourses__meta">
        <span>
          {{ course.level }}
        </span>
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
    course: {
      type: Object,
      required: true
    }
  },
  computed: {
    fromNow () {
      return this.$moment(this.course.createdAt).fromNow()
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
