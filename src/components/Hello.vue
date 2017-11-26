<template>
  <q-layout
    ref="layout"
    view="lHh Lpr fff"
    :left-class="{'bg-grey-2': true}"
  >
  <h1>{{message}}</h1>

  </q-layout>
</template>

<script>
import {
  QLayout
} from 'quasar'

export default {
  name: 'index',
  components: {
    QLayout
  },
  data () {
    return {
      message: 'hello'
    }
  }
}
</script>

<style lang="stylus">

</style>
