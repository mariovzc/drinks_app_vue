<template>
  <div>
    <q-list-header><strong>{{type}}</strong></q-list-header>
    <q-item 
      link 
      inset-separator
      v-for="(item, index) in items"
      :key="index"
    >
      <q-item-side>
      </q-item-side>
      <q-item-main 
        v-for="(value, key, index) in item" 
        :key="index"
        v-if="valid(value)"
      >
        <q-item-tile 
          label
          @click="goTo(value)"
        >{{value | capitalize}}</q-item-tile>
      </q-item-main>
    </q-item>
  </div>
</template>
<script>
import {
  QListHeader,
  QItemSeparator,
  QItemSide,
  QItemTile,
  QItemMain,
  QItem
} from 'quasar'
export default {
  props: ['type', 'url'],
  data () {
    return {
      items: []
    }
  },
  components: {
    QListHeader,
    QItemSeparator,
    QItemSide,
    QItemTile,
    QItemMain,
    QItem
  },
  methods: {
    fetchData () {
      this.items = []
      fetch(this.url, {
        method: 'GET'
      })
        .then(response => response.json())
        .then(json => (this.items = json.drinks))
    },
    goTo (to) {
      console.log(to)
    },
    valid (value) {
      if (value === '' || value === null) return false
      return true
    }
  },
  created () {
    this.fetchData()
  },
  filters: {
    capitalize: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.charAt(0).toUpperCase() + value.slice(1)
    }
  }
}
</script>
<style scoped>
.q-list-header {
  font-size: 25px;
}
.q-item {
  min-height: 70px;
}
</style>

