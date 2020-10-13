<template>
  <main class="page-category">
    <AppHeader>
      <h1 slot="title">
        {{ category.title }}
      </h1>
    </AppHeader>
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
