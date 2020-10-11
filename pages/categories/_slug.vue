<template>
  <main class="page-home">
    <section class="container">
      <h1>{{ category.title }}</h1>
    </section>
  </main>
</template>

<script>
export default {
  async asyncData ({ $axios, params }) {
    const { slug } = params
    const category = await $axios.$get('/api/categories/', { params: { slug } })
    return {
      category: category[0]
    }
  },
  head () {
    const { category } = this
    return {
      title: category.title
    }
  }
}
</script>
