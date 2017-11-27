<template>
  <div class="q-card" @click="goTo(drink.idDrink)">
    <div class="q-card-media relative-position">
      <img :src="drink.strDrinkThumb"> 
      <div class="q-card-media-overlay absolute-bottom">
        <div class="q-card-primary q-card-container row no-wrap">
          <div class="col column">
            <div class="q-card-title" >
              {{drink.strDrink}}
            </div>
            <div class="q-card-subtitle">
            </div>
          </div>
          <div class="col-auto self-center q-card-title-extra"></div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: ['drink'],
  methods: {
    goTo (id) {
      this.$router.push(`/detaileddrink/${id}`)
    }
  }
}
</script>
<style scoped>
.q-card{
  width: 100%;
  margin: 0px
}
</style>

