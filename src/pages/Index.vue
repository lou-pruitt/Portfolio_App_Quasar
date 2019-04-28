<template>
  <q-page class="row">
    <app-header></app-header>
    <app-about></app-about>
    <app-skills></app-skills>
    <app-projects></app-projects>
  </q-page>
</template>

<style>
</style>

<script>
export default {
  name: 'PageIndex',
  components: {
    appAbout: () => import('components/About.vue'),
    appHeader: () => import('components/Header.vue'),
    appProjects: () => import('components/Projects.vue'),
    appSkills: () => import('components/Skills.vue')
  }
}
</script>
