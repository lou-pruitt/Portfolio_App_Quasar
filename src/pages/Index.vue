<template>
  <q-page class="row">
    <app-header></app-header>
    <app-about></app-about>
    <app-skills></app-skills>
  </q-page>
</template>

<style>
</style>

<script>
// import appAbout from 'components/About.vue'
// import appHeader from 'components/Header.vue'
// import appSkills from 'components/Skills.vue'

export default {
  name: 'PageIndex',
  components: {
    appAbout: () => import('components/About.vue'),
    appHeader: () => import('components/Header.vue'),
    appSkills: () => import('components/Skills.vue')
  }
}
</script>
