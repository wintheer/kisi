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

.main-container {
  display: flex;
  justify-content: center;

  &__content {
    width: 80%;
  }
}
</style>