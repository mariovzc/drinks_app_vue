<template>
  <div class=" justify-center">
    <q-list multiline separator link>
      <q-item 
        v-for="(item, index) in items" 
        v-bind:key="index"
        @click="goToDetails(items.idDrink)"
      >
        <q-item-side :image="item.strDrinkThumb" />
        <q-item-main>
          <q-item-tile label>{{item.strDrink}}</q-item-tile>
        </q-item-main>
      </q-item>
    </q-list>
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

export default {
  data () {
    return {
      type: this.$route.params.type,
      items: []
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
        .then(json => (this.items = json.drinks))
    },
    goToDetails (id) {
      console.log(id)
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
    QItemTile
  }
}
</script>
<style scoped> 
.q-list{
  border: none;
}
</style>
