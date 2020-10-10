<template>
  <main class="page-home">
    <section class="container">
      <h1>{{ article.title }}</h1>
      <div class="content">
        {{ article.content }}
      </div>
    </section>
  </main>
</template>

<script>
export default {
  async asyncData ({ $http, params }) {
    const { slug } = params
    const article = await $http.$get('/api/articles/', { slug })
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
