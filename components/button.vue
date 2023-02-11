<template>
  <button @click="(event) => $emit('click', event)">{{ label }}</button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    label: {
      type: String,
      default: 'button'
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../static/assets/main.scss";

button {
  padding: 6px 20px;
  color: $white;
  font-size: inherit;
  background-color: $primary-color;
  border: none;
  border-radius: 20px;
  transition: background-color .2s;
  cursor: pointer;

  &:hover {
    background-color: darken($primary-color, 10%);
  }

  &:active {
    background-color: darken($primary-color, 5%);
  }
}
</style>