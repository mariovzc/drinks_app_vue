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
      this.type = this.$route.params.type
      fetch('http://www.thecocktaildb.com/api/json/v1/1/random.php', {
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
