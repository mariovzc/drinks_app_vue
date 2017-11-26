<template>
  <div class="layout text-center">
    <h3>Chose a Drink Type</h3>
    <div class="btn-list">
      <div class="btn-container">
        <router-link :to="{path: '/drinklist/Alcoholic'}">
          <q-btn class="bg-primary">
            Alcoholic
          </q-btn>
        </router-link>
      </div>
      <div class="btn-container">
        <router-link :to="{path: '/drinklist/Non_Alcoholic'}">
          <q-btn  class="bg-secondary">
            Non Alcoholic
          </q-btn>
        </router-link>
      </div>
      <div class="btn-container">
        <router-link :to="{path: '/randomdrink'}">
          <q-btn class="bg-tertiary">
            Random
          </q-btn>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
import {QBtn} from 'quasar'
export default {
  name: 'index',
  data () {
    return {
    }
  },
  components: {
    QBtn
  }
}
</script>

<style scoped>
  .layout{
    margin-top: 50px;
  }
  .btn-list{
    margin-top: 50px;
  }
  .btn-container{
    margin: 20px;
  }
  .btn-container button{
    color: #fff;
  }
</style>
