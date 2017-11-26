<template>
  <!-- Don't drop "q-app" class -->
  <div id="q-app">
    <q-layout
      ref="layout"
      :view="layoutStore.view"
      :left-breakpoint="layoutStore.leftBreakpoint"
      :reveal="layoutStore.reveal"
    >
      <q-toolbar slot="header">
        <q-btn flat @click="$refs.layout.toggleLeft()">
          <q-icon name="menu" />
        </q-btn>
        <q-toolbar-title>
          Drink Master
        </q-toolbar-title>
      </q-toolbar>
      <q-scroll-area slot="left" style="width: 100%; height: 100%">
        <q-list-header>Chose a Type</q-list-header>
        <q-side-link item to="/drinklist/Alcoholic">
          <q-item-main label="Alcoholic" />
        </q-side-link>
        <q-item-separator />
        <q-side-link item to="/drinklist/Non_Alcoholic">
          <q-item-main label="Non Alcoholic" />
        </q-side-link>
        <q-item-separator />
        <q-side-link item to="/randomdrink">
          <q-item-main label="Ramdon" />
        </q-side-link>
      </q-scroll-area>      
      <router-view />
    </q-layout>
  </div>
</template>

<script>
/*
 * Root component
 */
import {
  QLayout,
  QToolbar,
  QToolbarTitle,
  QSearch,
  QTabs,
  QRouteTab,
  QBtn,
  QIcon,
  QItemSide,
  QItemMain,
  QSideLink,
  QListHeader,
  QScrollArea,
  QItemSeparator
} from 'quasar'

import layoutStore from './layout-store'
export default {
  components: {
    QLayout,
    QToolbar,
    QToolbarTitle,
    QSearch,
    QTabs,
    QRouteTab,
    QBtn,
    QIcon,
    QItemSide,
    QItemMain,
    QSideLink,
    QListHeader,
    QScrollArea,
    QItemSeparator
  },
  data () {
    return {
      layoutStore
    }
  }
}
</script>

<style></style>
