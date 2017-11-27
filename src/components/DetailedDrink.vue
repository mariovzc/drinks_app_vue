<template>
  <div>
    <DetailedView 
    :drink="drink"/>
  </div>
</template>
<script>
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
      this.id = this.$route.params.id
      fetch(`http://www.thecocktaildb.com/api/json/v1/1/lookup.php?i=${this.id}`, {
        method: 'GET'
      })
        .then(response => response.json())
        .then(json => (this.drink = json.drinks[0]))
    }
  },
  created () {
    this.fetchItems()
  },
  components: {
    DetailedView
  }
}
</script>
