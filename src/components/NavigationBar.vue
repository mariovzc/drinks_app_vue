<template>
  <div>
    <q-toolbar slot="header" class= "toolbar">
      <q-btn
          flat
          v-if="canGoBack"
          @click="goBack"
          class="custon-btn"
        >
          <img src="../assets/img/back.svg" class="back-button">
        </q-btn>
        <q-btn 
          flat
          v-if="displayMenu"
        >
          <img src="../assets/img/menu-icon.svg" class="menu-icon">
        </q-btn>
    <q-toolbar-title to="/" class="nav-title" >
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
import layoutStore from './layout-store'

export default {
  props: ['title', 'displayMenu', 'canGoBack'],
  methods: {
    goBack () {
      window.history.go(-1)
    }
  },
  data () {
    return {
      layoutStore
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
.back-button{
  width: 26px;
  height: 26px;
}
.menu-icon{
  width: 20px;
  height: 20px;
}
.toolbar{
  background-color: #FFF;
}
.nav-title{
  color: #606060;
}
</style>
