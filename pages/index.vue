<template>
  <main class="page-home">
    <section class="container">
      <h2>Últimos artículos 📝</h2>
      <article v-for="article in articles" :key="article.title">
        <nuxt-link :to="{ name: 'slug', params: { slug: article.slug } }">
          {{ article.title }}
        </nuxt-link>
      </article>
    </section>
  </main>
</template>

<script>
export default {
  async asyncData ({ $http }) {
    const articles = await $http.$get('/api/articles/')
    return {
      articles
    }
  },
  head () {
    return {
      title: 'Inicio'
    }
  }
}
</script>
