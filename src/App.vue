<template>
  <!-- Don't drop "q-app" class -->
  <div id="q-app">
    <q-layout
      ref="layout"
    >      
      <router-view />
    </q-layout>
  </div>
</template>

<script>
/*
 * Root component
 */
import {
  QLayout
} from 'quasar'

export default {
  components: {
    QLayout
  }
}
</script>

<style></style>
