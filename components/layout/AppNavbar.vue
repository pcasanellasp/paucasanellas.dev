<template>
  <header class="AppNavbar">
    <div class="container">
      <div class="AppNavbar__section">
        <nuxt-link :to="{ name: 'index' }" class="AppNavbar__link AppNavbar__logo">
          paucasanellas.dev
        </nuxt-link>
      </div>
      <nav class="AppNavbar__section">
        <nuxt-link :to="{ name: 'index' }" class="AppNavbar__link">
          Inicio
        </nuxt-link>
      </nav>
    </div>
  </header>
</template>

<script>
export default {}
</script>

<style lang="scss">
.AppNavbar {
  margin-bottom: 2rem;

  .container {
    align-items: center;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }

  &__link {
    color: $gray-dark;
    display: inline-block;
    padding: 1rem;

    &:hover {
      text-decoration: none;
    }
  }

  &__logo {
    padding: 0;
  }
}
</style>
