<template>
  <div>
    <nav-bar :title="title"></nav-bar>
    <DetailedView 
    :drink="drink"/>
    <q-btn
      round
      small
      push
      color="primary"
      @click="newDrink"
      class="fixed"
      style="right: 18px; bottom: 18px"
      >
        <q-icon name="cached" />
      </q-btn>
  </div>
</template>
<script>
import {
  QBtn,
  QIcon
} from 'quasar'

import DetailedView from './DetailedView.vue'

import navBar from './NavigationBar.vue'

export default {
  data () {
    return {
      drink: {},
      title: 'Random Drink'
    }
  },
  methods: {
    fetchItems () {
      this.items = []
      this.type = this.$route.params.type
      fetch('http://www.thecocktaildb.com/api/json/v1/1/random.php', {
        method: 'GET'
      })
        .then(response => response.json())
        .then(json => (this.drink = json.drinks[0]))
    },
    newDrink () {
      this.fetchItems()
    }
  },
  created () {
    this.fetchItems()
  },
  components: {
    DetailedView,
    QBtn,
    QIcon,
    navBar
  }
}
</script>
