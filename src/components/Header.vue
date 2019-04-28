<template>
  <div class="q-pa-md col-12">
    <q-parallax>
      <template v-slot:media>
        <img v-if="$q.platform.is.mobile" src="statics\hb-pier-focus-mobile.png">
        <img v-if="$q.platform.is.desktop" src="statics\hb-pier-focus.png">
      </template>

      <template v-slot:content="scope">
        <div
          class="absolute column items-center"
          :style="{
            top: (scope.percentScrolled * 60) + '%',
            left: 0,
            right: 0
          }"
        >
          <img src="statics\pruitt_logo.png" style="width: 150px; height: 150px">
          <div class="text-h3 text-white text-center">{{ name }}</div>
          <div class="text-h6 text-white text-center">
            Web Developer
          </div>
        </div>
      </template>
    </q-parallax>
  </div>
</template>

<style>
</style>

<script>
export default {
  data () {
    return {
      name: 'Lou Pruitt'
    }
  }
}
</script>
