<template>
  <div>
    <nav-bar :title="drink.strDrink"></nav-bar>
    <div>
      <img :src="drink.strDrinkThumb" :alt="drink.strDrink" class="responsive">
    </div>
    <q-tabs>
      <!-- Tabs - notice slot="title" -->
      <q-tab default slot="title" name="details" label="Details" />
      <q-tab slot="title" name="instructions" label="Instructions" />
      <!-- Targets -->
      <q-tab-pane name="details">
        <q-list separator>
          <q-item>
            <q-item-main>
              <q-item-tile label class="text-center">Type: {{drink.strAlcoholic}}</q-item-tile>
            </q-item-main>
          </q-item>
          <q-item>
            <q-item-main>
              <q-item-tile label class="text-center">Glass Type: {{drink.strGlass}}</q-item-tile>
            </q-item-main>
          </q-item>
          <q-item class="table-item">
            <h5 class="text-center">Ingredients</h5>
            <table class="q-table striped-even">
              <tbody>
                <tr v-if="display(drink.strIngredient1)">
                  <td>{{drink.strIngredient1}}</td>
                  <td>{{drink.strMeasure1}}</td>
                </tr>
                <tr v-if="display(drink.strIngredient2)">
                    <td>{{drink.strIngredient2}}</td>
                    <td>{{drink.strMeasure2}}</td>
                </tr>
                <tr v-if="display(drink.strIngredient3)">
                  <td>{{drink.strIngredient3}}</td>
                  <td>{{drink.strMeasure3}}</td>          
                </tr>
                <tr v-if="display(drink.strIngredient4)">
                  <td>{{drink.strIngredient4}}</td>
                  <td>{{drink.strMeasure4}}</td>
                </tr>
                <tr v-if="display(drink.strIngredient5)">
                  <td>{{drink.strIngredient5}}</td>
                  <td>{{drink.strMeasure5}}</td>
                </tr>
                <tr v-if="display(drink.strIngredient6)">
                  <td>{{drink.strIngredient6}}</td>
                  <td>{{drink.strMeasure6}}</td>
                </tr>
                <tr v-if="display(drink.strIngredient7)">
                  <td>{{drink.strIngredient7}}</td>
                  <td>{{drink.strMeasure7}}</td>
                </tr>
                <tr v-if="display(drink.strIngredient8)">
                  <td>{{drink.strIngredient8}}</td>
                  <td>{{drink.strMeasure8}}</td>
                </tr>
                <tr v-if="display(drink.strIngredient9)">
                  <td>{{drink.strIngredient9}}</td>
                  <td>{{drink.strMeasure9}}</td>
                </tr>
                <tr v-if="display(drink.strIngredient10)">
                  <td>{{drink.strIngredient10}}</td>
                  <td>{{drink.strMeasure10}}</td>
                </tr>
                <tr v-if="display(drink.strIngredient11)">
                  <td>{{drink.strIngredient11}}</td>
                  <td>{{drink.strMeasure11}}</td>
                </tr>
                <tr v-if="display(drink.strIngredient12)">
                  <td>{{drink.strIngredient12}}</td>
                  <td>{{drink.strMeasure12}}</td>
                </tr>
                <tr v-if="display(drink.strIngredient13)">
                  <td>{{drink.strIngredient13}}</td>
                  <td>{{drink.strMeasure13}}</td>
                </tr>
                <tr v-if="display(drink.strIngredient14)">
                  <td>{{drink.strIngredient14}}</td>
                  <td>{{drink.strMeasure14}}</td>
                </tr>
                <tr v-if="display(drink.strIngredient15)">
                  <td >{{drink.strIngredient15}}</td>
                  <td>{{drink.strMeasure15}}</td>
                </tr>
              </tbody>
            </table>
          </q-item>
        </q-list>
      </q-tab-pane>
      <q-tab-pane name="instructions">
        <p class="light-paragraph">{{drink.strInstructions}}</p>
      </q-tab-pane>
    </q-tabs>
  </div>
</template>
<script>
import {
  QTabs,
  QTab,
  QTabPane,
  QList,
  QItem,
  QListHeader,
  QItemTile,
  QItemMain
} from 'quasar'
import navBar from './NavigationBar.vue'
export default {
  props: ['drink'],
  name: 'DetailedView',
  components: {
    QTabs,
    QTab,
    QTabPane,
    QList,
    QItem,
    QListHeader,
    QItemTile,
    QItemMain,
    navBar
  },
  methods: {
    display (value) {
      if (value === '' || value === null) return false
      return true
    }
  }
}
// strDrink = name , strCategory strAlcoholic, strGlass, strInstructions, strDrinkThumb
</script>
<style scoped>
table.q-table{
  text-align: center;
  width: 100%;
}
table.q-table thead{
  text-align: center;
}
.table-item{
  display: block;
}
</style>
