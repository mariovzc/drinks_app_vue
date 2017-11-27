<template>
  <div>
    <q-toolbar slot="header">
      <q-btn 
        flat 
        @click="goBack"
      >
        <q-icon v-if="canGoBack" name="back" />
      </q-btn>
    <q-toolbar-title to="/" class="text-center" >
    {{title}}
    </q-toolbar-title>
    </q-toolbar>
  </div>
</template>
<script>
import {
  QToolbar,
  QToolbarTitle,
  QBtn,
  QIcon
} from 'quasar'
export default {
  props: ['title'],
  data () {
    return {
      canGoBack: window.history.length > 1
    }
  },
  methods: {
    goBack () {
      window.history.go(-1)
    }
  },
  components: {
    QToolbar,
    QToolbarTitle,
    QBtn,
    QIcon
  }
}
</script>
