<template>
  <q-page class="row">
    <app-header></app-header>
    <app-about></app-about>
  </q-page>
</template>

<style>
</style>

<script>
import appAbout from 'components/About.vue'
import appHeader from 'components/Header.vue'

export default {
  name: 'PageIndex',
  components: {
    appAbout,
    appHeader
  }
}
</script>
