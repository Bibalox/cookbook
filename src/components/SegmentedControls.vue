<script setup>
defineProps({
  activeControl: {
    type: Number,
    default: 0
  }
})

defineEmits(['clickOnControl'])
</script>

<template>
  <div class="segmented-controls">
    <div class="segmented-controls__wrapper">
      <div
        :class="[
          'segmented-controls__active-marker',
          `segmented-controls__active-marker--position-${activeControl}`
        ]"
      />
      <button
        :class="[
          'segmented-controls__control',
          'label-md',
          { 'segmented-controls__control--active' : activeControl === 0 }
        ]"
        @click="$emit('clickOnControl', 0)"
      >
        Tout
      </button>
      <button
        :class="[
          'segmented-controls__control',
          'label-md',
          { 'segmented-controls__control--active' : activeControl === 1 }
        ]"
        @click="$emit('clickOnControl', 1)"
      >
        Salé
      </button>
      <button
        :class="[
          'segmented-controls__control',
          'label-md',
          { 'segmented-controls__control--active' : activeControl === 2 }
        ]"
        @click="$emit('clickOnControl', 2)"
      >
        Sucré
      </button>
    </div>
  </div>
</template>

<style lang="scss">
.segmented-controls {
  border-radius: 25px;
  background-color: var(--base-50);
  -webkit-backdrop-filter: blur(16px);
  backdrop-filter: blur(22px);
  box-shadow: 0px 2px 3px rgba(0, 0, 0, 0.05);
  box-sizing: border-box;
  flex-shrink: 0;
  height: 50px;
  max-width: 360px;
  padding: 4px;
  position: sticky;
  top: 0;
  width: 100%;
  z-index: 5000;

  &__wrapper {
    align-items: center;
    display: flex;
    height: 100%;
    position: relative;
    width: 100%;
  } 

  &__active-marker {
    background-color: var(--grey-solid-10);
    border-radius: 21px;
    box-shadow: 0px 3px 20px 3px rgba(0, 0, 0, 0.1), 0px 2px 4px rgba(0, 0, 0, 0.10);
    height: 100%;
    position: absolute;
    transition: transform .4s cubic-bezier(.65,0,.35,1);
    width: calc(100% / 3);
    z-index: 10;

    &--position-0 {
      transform: translateX(0);
    }

    &--position-1 {
      transform: translateX(100%);
    }

    &--position-2 {
      transform: translateX(200%);
    }
  }

  &__control {
    align-items: center;
    background-color: transparent;
    border: none;
    color: var(--grey-solid-80);
    cursor: pointer;
    display: flex;
    height: 100%;
    justify-content: center;
    outline: none;
    transition: color .2s ease-out .1s;
    width: calc(100% / 3);
    z-index: 20;

    &--active {
      color: var(--accent-solid-50);
    }
  }
}
</style>