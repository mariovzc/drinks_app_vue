<template>
  <!-- Don't drop "q-app" class -->
  <div id="q-app">
    <Header></Header>
    <router-view />
  </div>
</template>

<script>
/*
 * Root component
 */
import Header from './components/HeaderApp.vue'
export default {
  components: {
    Header
  }
}
</script>

<style></style>
