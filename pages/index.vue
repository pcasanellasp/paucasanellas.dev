<template>
  <main class="page-home">
    <AppHeader>
      <h1 slot="title" class="title">
        paucasanellas.dev
      </h1>
    </AppHeader>
    <section class="container">
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
  async asyncData ({ $axios }) {
    const articles = await $axios.$get('/api/articles/')
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
