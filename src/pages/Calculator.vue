<template>
  <div id="calculator" class="q-pa-md col-12 col-md-10 offset-md-1">
    <q-btn class="bg-white" to="/" glossy>Back to Portfolio</q-btn>
    <div class="row">
      <q-card id="calculatorCard" class="bg-grey text-white col-12">
        <q-card-section>
          <div>{{ display }}</div>
        </q-card-section>

        <q-card-actions class="row btnContainer">
          <div class="col-12">
            <div class="btnRow row justify-between">
              <q-btn @click="allClear" class="col-4 ac">AC</q-btn>
              <q-btn @click="clear" class="col-4 c">C</q-btn>
              <q-btn class="col-3 operator">/</q-btn>
            </div>
          </div>

          <div class="col-12">
            <div class="btnRow row">
              <q-btn @click="seven" class="col-3 number">7</q-btn>
              <q-btn @click="eight" class="col-3 number">8</q-btn>
              <q-btn @click="nine" class="col-3 number">9</q-btn>
              <q-btn class="col-3 operator">*</q-btn>
            </div>
          </div>

          <div class="col-12">
            <div class="btnRow row">
              <q-btn @click="four" class="col-3 number">4</q-btn>
              <q-btn @click="five" class="col-3 number">5</q-btn>
              <q-btn @click="six" class="col-3 number">6</q-btn>
              <q-btn class="col-3 operator">-</q-btn>
            </div>
          </div>

          <div class="col-12">
            <div class="btnRow row">
              <q-btn @click="one" class="col-3 number">1</q-btn>
              <q-btn @click="two" class="col-3 number">2</q-btn>
              <q-btn @click="three" class="col-3 number">3</q-btn>
              <q-btn class="col-3 operator">+</q-btn>
            </div>
          </div>

          <div class="col-12">
            <div class="btnRow row">
              <q-btn @click="zero" class="col-6 number">0</q-btn>
              <q-btn class="col-3 decimal">.</q-btn>
              <q-btn class="col-3 equals">=</q-btn>
            </div>
          </div>
        </q-card-actions>
      </q-card>
    </div>
  </div>
</template>

<style scoped>
  #ac, #c {
    background-color: #ded8d8;
  }
  .operator, .equals {
    background-color: burlywood;
  }
  .number, .decimal {
    background-color: cornflowerblue;
  }
</style>

<script>
export default {
  data: function () {
    return {
      display: '0'
    }
  },
  methods: {
    allClear () {
      this.display = '0'
    },
    clear () {
      if (this.display.length === 1 || this.display === '0') {
        this.display = '0'
        return
      }
      this.display = this.display.substring(0, this.display.length - 1)
    },
    one () {
      if (this.display === '0') {
        this.display = ''
      }
      this.display += '1'
    },
    two () {
      if (this.display === '0') {
        this.display = ''
      }
      this.display += '2'
    },
    three () {
      if (this.display === '0') {
        this.display = ''
      }
      this.display += '3'
    },
    four () {
      if (this.display === '0') {
        this.display = ''
      }
      this.display += '4'
    },
    five () {
      if (this.display === '0') {
        this.display = ''
      }
      this.display += '5'
    },
    six () {
      if (this.display === '0') {
        this.display = ''
      }
      this.display += '6'
    },
    seven () {
      if (this.display === '0') {
        this.display = ''
      }
      this.display += '7'
    },
    eight () {
      if (this.display === '0') {
        this.display = ''
      }
      this.display += '8'
    },
    nine () {
      if (this.display === '0') {
        this.display = ''
      }
      this.display += '0'
    },
    zero () {
      if (this.display === '0') {
        return
      }
      this.display += '0'
    }
  }
}
</script>
