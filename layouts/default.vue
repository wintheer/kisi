<template>
  <div class="main">
    <div class="header"></div>

    <Nuxt />
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
  background-color: $background-color;
}
</style>