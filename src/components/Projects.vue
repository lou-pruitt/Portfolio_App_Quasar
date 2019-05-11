<template>
  <div id="projects" class="q-pa-md col-12 col-md-10 offset-md-1">
    <q-card flat bordered class="skills-card text-center">
      <q-card-section>
        <div class="text-h6">Projects</div>
      </q-card-section>

      <q-separator color="blue" inset/>

      <div class="row">
        <q-card class="projectCard col-12 col-md-4 q-pa-sm">
          <q-img src="statics\snack-seriously.png">
            <div class="absolute-bottom">
              <div class="text-h6">SnackSeriously.com</div>
              <div class="text-subtitle2">Find a snack</div>
            </div>
          </q-img>
          <q-card-actions>
            <q-btn @click="snackLink" glossy>Try it</q-btn>
            <q-btn @click="snackGithub" glossy>Github</q-btn>
          </q-card-actions>
        </q-card>

        <q-card class="projectCard col-12 col-md-4 q-pa-sm">
          <q-img src="statics\calculator.png">
            <div class="absolute-bottom">
              <div class="text-h6">Calculator</div>
              <div class="text-subtitle2">Basic calculator</div>
            </div>
          </q-img>
          <q-card-actions>
            <q-btn to="calculator" glossy>Try it</q-btn>
            <q-btn glossy>Github</q-btn>
          </q-card-actions>
          <div class="text-center">Links coming soon</div>
        </q-card>

        <q-card class="projectCard col-12 col-md-4 q-pa-sm">
          <q-img src="statics\match.png">
            <div class="absolute-bottom">
              <div class="text-h6">Match The Cats</div>
              <div class="text-subtitle2">Memory matching game with cats</div>
            </div>
          </q-img>
          <q-card-actions>
            <q-btn glossy>Try it</q-btn>
            <q-btn glossy>Github</q-btn>
          </q-card-actions>
          <div class="text-center">Links coming soon</div>
        </q-card>
      </div>
    </q-card>
  </div>
</template>

<style>
</style>

<script>
export default {
  methods: {
    snackLink: function () {
      window.open('https://snackseriously.com/', '_blank')
    },
    snackGithub: function () {
      window.open('https://github.com/Patriciadburns1/snack_seriously', '_blank')
    }
  }
}
</script>
