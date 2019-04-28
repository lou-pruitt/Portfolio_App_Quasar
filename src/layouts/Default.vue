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
          <q-list v-for="(pageItem, index) in pageList" :key="index">
            <q-item v-if="!pageItem.site" :to="`#${pageItem.link}`" clickable v-ripple>
              <q-item-section avatar>
                <q-icon :name="pageItem.icon" />
              </q-item-section>
              <q-item-section>
                {{ pageItem.label }}
              </q-item-section>
            </q-item>

            <q-item v-if="pageItem.site" @click="linkTo" clickable v-ripple>
              <q-item-section avatar>
                <q-icon :name="pageItem.icon" />
              </q-item-section>
              <q-item-section>
                {{ pageItem.label }}
              </q-item-section>
            </q-item>

           <q-separator v-if="pageItem.separator" />

          </q-list>
        </q-scroll-area>
      </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
const pageList = [
  {
    icon: 'fas fa-address-card',
    label: 'About',
    link: 'about',
    separator: false,
    site: false
  },
  {
    icon: 'fas fa-toolbox',
    label: 'Skills/Tools',
    link: 'skills',
    separator: false,
    site: false
  },
  {
    icon: 'fas fa-laptop-code',
    label: 'Projects',
    link: 'projects',
    separator: true,
    site: false
  },
  {
    icon: 'fas fa-envelope',
    label: 'Contact Me',
    link: 'contact',
    separator: false,
    site: true
  },
  {
    icon: 'fab fa-github',
    label: 'Github',
    link: 'https://github.com/Chyort',
    separator: false,
    site: true
  },
  {
    icon: 'fab fa-linkedin',
    label: 'LinkedIn',
    link: 'linkedIn',
    separator: false,
    site: true
  },
  {
    icon: 'fas fa-graduation-cap',
    label: 'Education',
    link: 'learningFuze',
    separator: true,
    site: true
  }
]

export default {
  data () {
    return {
      drawer: true,
      pageList
    }
  },
  methods: {
    linkTo: function () {
      window.open('https://github.com/Chyort', '_blank')
    },
    linkedIn: function () {
      window.open('www.linkedin.com/in/herbert-luis-pruitt', '_blank')
    },
    fuze: function () {
      window.open('https://learningfuze.com/about-us', '_blank')
    }
  }
}
</script>

<style>
</style>
