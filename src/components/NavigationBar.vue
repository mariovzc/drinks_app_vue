<template>
  <div>
    <q-toolbar slot="header">
      <q-btn
          flat
          v-if="canGoBack"
          color="primary"
          @click="goBack"
          icon="keyboard_arrow_left"
          class="custon-btn"
        >
        </q-btn>
    <q-toolbar-title to="/" >
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
<style scoped>
button{
  color: white !important;
}
</style>
