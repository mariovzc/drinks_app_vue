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
          :sufix="type.type"
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
          type: 'a='
        },
        {
          name: 'Category',
          type: 'c='
        },
        {
          name: 'Glass',
          type: 'g='
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