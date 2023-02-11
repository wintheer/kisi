<template>
  <div class="main-container">
    <div class="main-container__content">
      <Nuxt />
    </div>
  </div>
</template>

<script>
export default {
  name: 'MainLayout'
};
</script>

<style lang="scss" scoped>
@import "../static/assets/main.scss";
.main {
  height: 100vh;
}

// Use grid for small laptop sizes and up
@media only screen and (min-width: 769px) {
  .main-container {
    display: flex;
    justify-content: center;

    &__content {
      width: 80%;
    }
  }
}
</style>