<template>
  <main class="page-article">
    <AppHeader>
      <h1 slot="title">
        {{ article.title }}
      </h1>
    </AppHeader>
    <section class="container">
      {{ article.content }}
    </section>
  </main>
</template>

<script>
export default {
  async asyncData ({ $axios, params }) {
    const { slug } = params
    const article = await $axios.$get('/api/articles/', { params: { slug } })
    return {
      article: article[0]
    }
  },
  head () {
    const { article } = this
    return {
      title: article.title
    }
  }
}
</script>
