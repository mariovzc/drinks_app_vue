<template>
  <div>
    <q-list-header><strong>{{type}}</strong></q-list-header>
    <q-item 
      link 
      separator
      v-for="(item, index) in items"
      :key="index"
    >
      <div
        v-for="(value, key, index) in item" 
        :key="index"
        v-if="valid(value)"
        class="cnt"
      >
        <q-item-side></q-item-side>
        <q-item-main         
        >
          <q-item-tile 
            label
            @click="goTo(value, sufix)"
          >{{value | capitalize}}</q-item-tile>
        </q-item-main>
        <q-item-side right icon="keyboard_arrow_right"  />
      </div>
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
  props: ['type', 'sufix'],
  data () {
    return {
      items: [],
      url: 'http://www.thecocktaildb.com/api/json/v1/1/list.php?'
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
      fetch(this.url + this.sufix + 'list', {
        method: 'GET'
      })
        .then(response => response.json())
        .then(json => {
          this.items = json.drinks

          if (this.type === 'Alcoholic') {
            this.items.splice(-1, 1)
          }
        })
    },
    goTo (name, sufix) {
      this.$router.push({
        path: '/drinklist/',
        query: {
          type: name,
          sufix: sufix
        }
      })
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
.cnt{
  width: 100%;
  display: inline-flex;
  display: -webkit-inline-flex;
  height: 100%;
}
</style>

