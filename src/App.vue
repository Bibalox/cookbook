<script setup>
import { RouterView } from 'vue-router'
import './variables/colors.scss'
import './variables/fonts.scss'

import BackgroundImage from './components/BackgroundImage.vue'

const init = async () => {
  try {
    await navigator.wakeLock.request('screen')
  } catch (err) {
    console.error('Screen wake lock cannot be activated')
  }
}

init()
</script>

<template>
  <background-image
    src="/images/home-background.jpeg"
    blurry
  />
  <router-view />
</template>

<style lang="scss">
html {
  height: calc(100% + env(safe-area-inset-top));
}

body {
  background-color: var(--grey-solid-10);
  margin: 0;
  height: 100%;
  padding: 0;
  position: fixed;
  width: 100%;
}

button, a {
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}

#app {
  height: 100%;
}
</style>