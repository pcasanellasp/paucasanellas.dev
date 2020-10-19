<template>
  <main class="page-explore">
    <AppHeader>
      <h1 slot="title" class="title">
        Explorar
      </h1>
    </AppHeader>
    <section class="container">
      <CategoryItem v-for="category in categories" :key="category.title" :category="category" />
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
