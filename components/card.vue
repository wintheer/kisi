<template>
  <div @mouseenter="hovering = true" @mouseleave="hovering = false">
    <img :src="backgroundImagePath" alt="background image" />
    <slot name="header"></slot>
    <div>
      <slot name="description"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    headerText: {
      type: String,
      default: ''
    },
    backgroundImagePath: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      hovering: false
    };
  }
};
</script>

<style lang="scss" scoped>
</style>