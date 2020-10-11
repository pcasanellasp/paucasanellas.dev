<template>
  <footer class="AppNavbar">
    <div class="container">
      <nuxt-link :to="{ name: 'index' }" class="AppNavbar__link">
        <IconHomeOutline width="24" />
      </nuxt-link>
      <nuxt-link :to="{ name: 'explore' }" class="AppNavbar__link">
        <IconCompassOutline width="24" />
      </nuxt-link>
      <nuxt-link :to="{ name: 'search' }" class="AppNavbar__link">
        <IconSearchOutline width="24" />
      </nuxt-link>
      <nuxt-link :to="{ name: 'admin' }" class="AppNavbar__link">
        <IconPersonOutline width="24" />
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

  .container {
    display: flex;
    flex-wrap: nowrap;
    justify-content: space-around;

  }

  &__link {
    display: block;
    padding: 0.5rem 2rem;
    padding-top: 1rem;
    transition: all .5s;
    border-bottom: 5px solid transparent;

    &.nuxt-link-exact-active {
      border-bottom-color: $blue-400;
      .icon {
        color: $gray-800;
        fill: $gray-800;
      }
    }
  }

  .icon {
    color: $gray-200;
    fill: $gray-200;
  }
}
</style>
