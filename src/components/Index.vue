<template>
  <div>
    <q-toolbar slot="header">
      <q-toolbar-title to="/" class="text-center" >
      {{title}}
      </q-toolbar-title>
    </q-toolbar>
    <div class="layout">
      <q-list no-border>

        <drinks-types 
          v-for="(type, index) in types"
          :key="index"
          :type="type.name"
          :separator="true"
          :url="type.url"
        >
        </drinks-types>
      </q-list>
    </div>    
  </div>
</template>

<script>
import {
  QToolbar,
  QToolbarTitle,
  QList
} from 'quasar'
import DrinksTypes from './DrinksTypes.vue'

export default {
  name: 'index',
  data () {
    return {
      title: 'Drink Master',
      types: [
        {
          name: 'Alcoholic',
          url: 'http://www.thecocktaildb.com/api/json/v1/1/list.php?a=list'
        },
        {
          name: 'Category',
          url: 'http://www.thecocktaildb.com/api/json/v1/1/list.php?c=list'
        },
        {
          name: 'Glass',
          url: 'http://www.thecocktaildb.com/api/json/v1/1/list.php?g=list'
        }
      ]
    }
  },
  components: {
    QToolbar,
    QToolbarTitle,
    QList,
    DrinksTypes
  }
}
</script>