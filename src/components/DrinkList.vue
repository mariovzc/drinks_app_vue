<template>
  <div>
    <nav-bar :title="`${titelize()} Drink's`"></nav-bar>
      <card-view
        v-for="(drink, index) in drinks"
        v-bind:key="index"
        :drink="drink"
      >
      </card-view>
    </div>
  </div>
</template>
<script>
import {
  QList,
  QListHeader,
  QItem,
  QItemSeparator,
  QItemSide,
  QItemMain,
  QItemTile
} from 'quasar'

import CardView from './CardView.vue'
import navBar from './NavigationBar.vue'

export default {
  data () {
    return {
      type: this.$route.params.type,
      drinks: []
    }
  },
  watch: {
    '$route': 'fetchItems'
  },
  methods: {
    fetchItems () {
      this.items = []
      this.type = this.$route.params.type
      fetch(`http://www.thecocktaildb.com/api/json/v1/1/filter.php?a=${this.type}`, {
        method: 'GET'
      })
        .then(response => response.json())
        .then(json => (this.drinks = json.drinks))
    },
    titelize () {
      return this.type.replace('_', ' ')
    }
  },
  created () {
    this.fetchItems()
  },
  components: {
    QList,
    QListHeader,
    QItem,
    QItemSeparator,
    QItemSide,
    QItemMain,
    QItemTile,
    navBar,
    CardView
  }
}
</script>
<style scoped> 
body{
  background-color: rgba(0,0,0,0.47)
}
</style>
