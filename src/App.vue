<template>
  <!-- Don't drop "q-app" class -->
  <div id="q-app">
    <q-layout
      ref="layout"
      :view="layoutStore.view"
      :left-breakpoint="layoutStore.leftBreakpoint"
      :reveal="layoutStore.reveal"
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

import layoutStore from './layout-store'
export default {
  components: {
    QLayout
  },
  data () {
    return {
      layoutStore
    }
  }
}
</script>

<style></style>
