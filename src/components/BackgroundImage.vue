<script setup>
defineProps({
  src: {
    type: String,
    required: true
  },
  blurry: {
    type: Boolean,
    default: false
  }
})
</script>

<template>
  <div class="background-image">
    <img
      class="background-image__image"
      :class="[{ 'background-image__image--blurry' : blurry }]"
      :src="src"
    >
  </div>
</template>

<style lang="scss">
.background-image {
  height: 110%;
  left: 0;
  max-height: 900px;
  overflow: hidden;
  position: absolute;
  top: 0;
  width: 110%;
  z-index: -1;

  &__image {
    height: 100%;
    object-fit: cover;
    -webkit-mask-image: linear-gradient(transparent 5%, black 50%, transparent 90%);
    mask-image: linear-gradient(transparent 5%, black 50%, transparent 90%);
    width: 100%;

    &--blurry {
      $blur: 8px;

      filter: blur($blur);
      height: calc(100% + 4 * $blur);
      opacity: .8;
      transform: translate(-2 * $blur, -2 * $blur);
      width: calc(100% + 4 * $blur);
    }
  }
}
</style>