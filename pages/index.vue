<template>
  <main class="page-home">
    <AppHeader>
      <h1 slot="title">
        Pau Casanellas
      </h1>
    </AppHeader>
    <SectionBlock to="articles">
      <h3 slot="title">
        Últimos artículos
      </h3>
      <template slot="content">
        <LastPostsItem v-for="article in articles" :key="article.title" :article="article" />
      </template>
    </SectionBlock>
    <SectionBlock to="articles">
      <h3 slot="title">
        Cursos destacados
      </h3>
      <template slot="content">
        <carousel :per-page-custom="[[320, 1],[720, 3]]" :autoplay="true">
          <slide v-for="article in articles" :key="article.title">
            <FeatureCourses :article="article" />
          </slide>
        </carousel>
      </template>
    </SectionBlock>
  </main>
</template>

<script>
export default {
  async asyncData ({ $axios }) {
    const articles = await $axios.$get('/api/articles/', { params: { _limit: 5 } })
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
