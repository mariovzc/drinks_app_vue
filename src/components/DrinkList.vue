<template>
  <div>
    <nav-bar 
      :title="`${this.type} Drink's`"
      :canGoBack = "true"
      :display-menu="false"
    ></nav-bar>
    <div class="row">
      <card-view
      v-for="(drink, index) in drinks"
      v-bind:key="index"
      :drink="drink"
      >
      </card-view>
    </div>
    <q-btn
      v-back-to-top.animate="{offset: 500, duration: 200}"
      round
      class="fixed-bottom-right animate-pop back-top-btn"
      style="margin: 0 15px 15px 0"      
    >
      <q-icon name="keyboard_arrow_up" />
    </q-btn>
  </div>
</template>
<script>
import {
  QBtn,
  QIcon,
  BackToTop,
  Ripple,
  Loading,
  QCard,
  QCardTitle,
  QCardMedia,
  QCardActions,
  QCardSeparator,
  QCardMain,
  QList,
  QItem,
  QItemMain,
  QItemSide,
  QItemTile,
  QCollapsible
} from 'quasar'

import CardView from './CardView.vue'
import NavBar from './NavigationBar.vue'

export default {
  data () {
    return {
      type: this.$route.query.type,
      sufix: this.$route.query.sufix,
      drinks: []
    }
  },
  watch: {
    '$route': 'fetchItems'
  },
  methods: {
    fetchItems () {
      this.items = []
      this.type = this.$route.query.type
      this.sufix = this.$route.query.sufix
      fetch(`http://www.thecocktaildb.com/api/json/v1/1/filter.php?${this.sufix}${this.type}`, {
        method: 'GET'
      })
        .then(response => response.json())
        .then(json => (this.drinks = json.drinks))
    },
    titelize () {
      return this.type.replace('_', ' ')
    }
  },
  beforeCreate () {
    Loading.show()
  },
  created () {
    this.fetchItems()
  },
  components: {
    NavBar,
    CardView,
    QBtn,
    QIcon,
    QCard,
    QCardTitle,
    QCardMedia,
    QCardActions,
    QCardSeparator,
    QCardMain,
    QList,
    QItem,
    QItemMain,
    QItemSide,
    QItemTile,
    QCollapsible
  },
  directives: {
    BackToTop,
    Ripple
  },
  updated () {
    Loading.hide()
  }
}
</script>
<style scoped> 
.back-top-btn{
  background-color: #5FAF50;
  color: #fff;
}
</style>
