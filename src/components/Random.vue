<template>
  <div>
    <DetailedView 
    :drink="drink"/>
    <q-btn
      round
      color="primary"
      @click="newDrink"
      class="fixed"
      style="right: 18px; bottom: 18px"
      >
        <q-icon name="mail" />
      </q-btn>
  </div>
</template>
<script>
import {QBtn, QIcon} from 'quasar'
import DetailedView from './DetailedView.vue'
export default {
  data () {
    return {
      drink: {}
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
    QIcon
  }
}
</script>
