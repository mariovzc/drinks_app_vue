<template>
  <div>
    {{drink}}
  </div>
</template>
<script>
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
        .then(json => (this.drink = json.drinks))
    }
  },
  created () {
    this.fetchItems()
  }
}
</script>
