<template>
  <section class="SectionBlock">
    <div class="container content">
      <slot name="title" />
      <slot name="content" />
      <p v-if="to" class="text-right">
        <nuxt-link :to="{ name: 'articles'} ">
          Ver más...
        </nuxt-link>
      </p>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    to: {
      type: String,
      default: null
    }
  }
}
</script>

<style>
.SectionBlock {
  margin-bottom: 3rem;
}
</style>
