<template>
  <div class="relative" @mouseenter="hovering = true" @mouseleave="hovering = false">
    <div class="image-container">
      <div class="image-overlay"></div>
      <img class="image" :src="backgroundImagePath" alt="background image" />
    </div>
    <div class="header">
      <slot name="header"></slot>
    </div>
    <div class="hover-container" :class="{ hidden: !hovering }">
      <slot name="description"></slot>
    </div>
    <img class="arrow" :src="icons.angle" alt="arrow right" />
  </div>
</template>

<script>
import angle from './../static/icons/arrow-down-angle.svg';
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
      hovering: false,
      icons: {
        angle
      }
    };
  }
};
</script>

<style lang="scss" scoped>
@import '../static/assets/main.scss';
.image {
  width: 100%;
  height: inherit;
  border-radius: 4px;

  object-fit: cover;

  &-overlay {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 1;
    background-color: rgba(#000, 0.2);
  }
}

.image-container {
  height: 100%;
}

.header {
  position: absolute;
  top: 10px;
  left: 20px;
  z-index: 3;
}

.hover-container {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 2;
  padding-top: 80px;
  padding-left: 20px;
  background-color: $card-hover;
  border-radius: 4px;
  transition: opacity 0.2s;
  opacity: 1;

  &.hidden {
    opacity: 0;
  }

  & span {
    padding-top: 50px;
  }
}

.arrow {
  position: absolute;
  right: 15px;
  bottom: 15px;
  z-index: 3;
  height: 15px;
  transform: rotate(-90deg);
  filter: brightness(0) invert(1);

  &:hover {
    transform: rotate(-90deg) scale(1.1);
  }
}
</style>