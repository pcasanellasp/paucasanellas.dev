<template>
  <main class="page-explore">
    <section class="container">
      <h2>Categorías</h2>
      <article v-for="category in categories" :key="category.title">
        <nuxt-link :to="{ name: 'categories-slug', params: { slug: category.slug } }">
          {{ category.title }}
        </nuxt-link>
      </article>
    </section>
  </main>
</template>

<script>
export default {
  async asyncData ({ $axios }) {
    const categories = await $axios.$get('/api/categories/')
    return {
      categories
    }
  },
  head () {
    return {
      title: 'Categorías'
    }
  }
}
</script>
