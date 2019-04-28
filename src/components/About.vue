<template>
  <div id="about" class="q-pa-md col-12 col-md-10 offset-md-1">
    <q-card dark bordered class="bg-accent about-card">
      <q-card-section class="text-center">
        <div class="text-h6">About Me</div>
        <div class="text-subtitle2">Losing and regaining my passion in the tech industry</div>
      </q-card-section>

      <q-separator color="primary" inset/>

      <q-card-section>
        {{ paragraph1 }}
      </q-card-section>

      <q-card-section>
        {{ paragraph2 }}
      </q-card-section>
    </q-card>
  </div>
</template>

<style>

</style>

<script>
export default {
  data () {
    return {
      paragraph1: 'I am a web developer based in Orange County. I studied computer electronics at Devry University. Having lost interest in the hardware aspect of computing, I believed that a future in tech was not for me. It wasn\'t until my then fiance asked me about my career aspirations. After hearing about my former interests, she recommended looking into programming.',
      paragraph2: 'After figuring out how to trace a "For" loop, a huge sense of accomplishment kept me wanting to learn more about programming. Since then, I have completed an immersive web development course and have the capability to create website applications from nothing. My goal is to create a personalized mobile app that is convenient and efficient for small companies to interact with their clients. In my spare time I enjoy surfing and archery, both of which I am self-taught.'
    }
  }
}
</script>
