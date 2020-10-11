<template>
  <footer class="AppNavbar">
    <div class="container">
      <nuxt-link :to="{ name: 'index' }" class="AppNavbar__link">
        <IconHomeOutline width="20" />
        <p>Inicio</p>
      </nuxt-link>
      <nuxt-link :to="{ name: 'explore' }" class="AppNavbar__link">
        <IconCompassOutline width="20" />
        <p>Explorar</p>
      </nuxt-link>
      <nuxt-link :to="{ name: 'search' }" class="AppNavbar__link">
        <IconSearchOutline width="20" />
        <p>Buscar</p>
      </nuxt-link>
      <nuxt-link :to="{ name: 'admin' }" class="AppNavbar__link">
        <IconSettingsOutline width="20" />
        <p>Ajustes</p>
      </nuxt-link>
    </div>
  </footer>
</template>

<script>
export default {}
</script>

<style lang="scss">
.AppNavbar {
  bottom: 0;
  margin-top: 2rem;
  position: fixed;
  width: 100%;
  border-top: 1px solid $gray-200;

  .container {
    display: flex;
    flex-wrap: nowrap;
    justify-content: space-around;
  }

  &__link {
    display: block;
    padding: 0.25rem 1.25rem;
    padding-top: 1rem;
    transition: all 1s;
    border-bottom: 5px solid transparent;
    text-align: center;
    color: $gray-400;

    p {
      font-size: 0.75rem;
    }

    &:focus {
      text-decoration: none;
      outline: 0;
    }

    &.nuxt-link-exact-active {
      .icon,
      p {
        transition: all .5s;
        color: $purple-400;
        fill: $purple-400;
      }
    }
  }

  .icon {
    fill: $gray-400;
  }
}
</style>
