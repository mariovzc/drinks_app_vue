<template>
  <div class="col-6 col-md-6 col-lg-3 ctn">
    <q-card inline>
      <q-card-media>
        <img :src="drink.strDrinkThumb"> 
      </q-card-media>
      <q-card-title>
        {{drink.strDrink | wordbreaker}}
      </q-card-title>
      <q-card-separator />
      <q-card-actions >
        <q-btn 
          flat
          @click="goTo(drink.idDrink)"
        >
          Preparation
        </q-btn>
      </q-card-actions>
    </q-card>
  </div>
</template>
<script>
import {
  QCard,
  QCardMedia,
  QCardTitle,
  QBtn,
  QCardActions,
  QCardSeparator,
  QCardMain
} from 'quasar'
export default {
  props: ['drink'],
  methods: {
    goTo (id) {
      this.$router.push(`/detaileddrink/${id}`)
    }
  },
  components: {
    QCard,
    QCardMedia,
    QCardTitle,
    QBtn,
    QCardActions,
    QCardSeparator,
    QCardMain
  },
  filters: {
    wordbreaker: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.substring(0, 10) + '...'
    }
  }
}
</script>
<style scoped>
.cnt {
  margin-top: 20px;
}
.q-card {
  background-color: #FFF;
  box-shadow: 0 0px 0px rgba(0,0,0,0.2), 0 0px 0px rgba(0,0,0,0.14), 0 0.8px .9px .9px rgba(0,0,0,0.12);
}
.q-card-title{
  color: #373737;
  /*height: 372px;**/
}
.q-btn{
  width: 100%;
  color: #449534;
}
</style>

