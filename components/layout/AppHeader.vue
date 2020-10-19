<template>
  <header class="AppHeader">
    <div class="container">
      <div class="AppHeader__section">
        <slot name="title" />
      </div>
    </div>
  </header>
</template>

<script>
export default {}
</script>

<style lang="scss">
.AppHeader {
  margin-bottom: 2rem;
  padding: 1.25rem 0;
  .container {
    align-items: center;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }

  .title {
    font-weight: bold;
  }
}
</style>
