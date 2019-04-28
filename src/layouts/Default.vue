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
          <q-list v-for="(pageItem, link) in pageList" :key="link">
            <q-item v-if="!pageItem.site" :to="`#${pageItem.link}`" clickable v-ripple>
              <q-item-section avatar>
                <q-icon :name="pageItem.icon" />
              </q-item-section>
              <q-item-section>
                {{ pageItem.label }}
              </q-item-section>
            </q-item>

            <q-item v-else-if="pageItem.site" @click="linkTo" clickable v-ripple>
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
export default {
  data () {
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
        label: 'Contact',
        link: 'mailTo:louPruitt.dev@gmail.com',
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
        link: 'www.linkedin.com/in/herbert-luis-pruitt',
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
    return {
      drawer: true,
      pageList
    }
  },
  methods: {
    linkTo: function (link) {
      if (link.toElement.innerText === 'Contact') {
        window.open('mailTo:louPruitt.dev@gmail.com')
      } else if (link.toElement.innerText === 'Github') {
        window.open('https://github.com/Chyort', '_blank')
      } else if (link.toElement.innerText === 'LinkedIn') {
        window.open('https://www.linkedin.com/in/herbert-luis-pruitt', '_blank')
      } else if (link.toElement.innerText === 'Education') {
        window.open('https://learningfuze.com/about-us', '_blank')
      }
    }
  }
}
</script>

<style>
</style>
