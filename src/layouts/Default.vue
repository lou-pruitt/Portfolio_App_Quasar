<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="glossy">
      <q-toolbar class="text-center">
        <q-btn
          flat
          dense
          round
          @click="drawer = !drawer"
          aria-label="Menu"
        >
          <q-icon name="menu" />
        </q-btn>

        <q-toolbar-title>
          Lou Pruitt - Portfolio
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer
        v-model="drawer"
        :width="200"
        :breakpoint="500"
        show-if-above
        elevated
        content-class="bg-secondary"
      >
        <q-scroll-area class="fit">
          <q-list v-for="(menuItem, index) in menuList" :key="index">

            <q-item clickable v-ripple>
              <q-item-section avatar>
                <q-icon :name="menuItem.icon" />
              </q-item-section>
              <q-item-section>
                {{ menuItem.label }}
              </q-item-section>
            </q-item>

           <q-separator v-if="menuItem.separator" />

          </q-list>
        </q-scroll-area>
      </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
const menuList = [
  {
    icon: 'fas fa-address-card',
    label: 'About',
    separator: false
  },
  {
    icon: 'fas fa-toolbox',
    label: 'Skills/Tools',
    separator: false
  },
  {
    icon: 'fas fa-laptop-code',
    label: 'Projects',
    separator: false
  },
  {
    icon: 'fas fa-envelope',
    label: 'Contact Me',
    separator: true
  },
  {
    icon: 'fab fa-github',
    label: 'Github',
    separator: false
  },
  {
    icon: 'fab fa-linkedin',
    label: 'LinkedIn',
    separator: false
  },
  {
    icon: 'fas fa-graduation-cap',
    label: 'Education',
    separator: true
  }
]

export default {
  data () {
    return {
      drawer: true,
      menuList
    }
  }
}
</script>

<style>
</style>
