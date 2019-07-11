<template>
  <div id="calculator" class="q-pa-md col-12 col-md-10 offset-md-1">
    <q-btn class="bg-white" to="/" glossy>Back to Portfolio</q-btn>
    <div class="row">
      <q-card id="calculatorCard" class="bg-grey text-white col-12">
        <q-card-section>
          <!-- <div>{{ display }}</div> -->
          <input type="text" :value="display" class="display" disabled>
        </q-card-section>

        <q-card-actions class="row btnContainer">
          <div class="col-12">
            <div class="btnRow row justify-between">
              <q-btn @click="allClear" class="col-4 ac">AC</q-btn>
              <q-btn @click="clear" class="col-4 c">C</q-btn>
              <q-btn @click="operator" class="col-3 operator">/</q-btn>
            </div>
          </div>

          <div class="col-12">
            <div class="btnRow row">
              <q-btn @click="number" class="col-3 number">7</q-btn>
              <q-btn @click="number" class="col-3 number">8</q-btn>
              <q-btn @click="number" class="col-3 number">9</q-btn>
              <q-btn @click="operator" class="col-3 operator">*</q-btn>
            </div>
          </div>

          <div class="col-12">
            <div class="btnRow row">
              <q-btn @click="number" class="col-3 number">4</q-btn>
              <q-btn @click="number" class="col-3 number">5</q-btn>
              <q-btn @click="number" class="col-3 number">6</q-btn>
              <q-btn @click="operator" class="col-3 operator">-</q-btn>
            </div>
          </div>

          <div class="col-12">
            <div class="btnRow row">
              <q-btn @click="number" class="col-3 number">1</q-btn>
              <q-btn @click="number" class="col-3 number">2</q-btn>
              <q-btn @click="number" class="col-3 number">3</q-btn>
              <q-btn @click="operator" class="col-3 operator">+</q-btn>
            </div>
          </div>

          <div class="col-12">
            <div class="btnRow row">
              <q-btn @click="zero" class="col-6 number">0</q-btn>
              <q-btn class="col-3 decimal">.</q-btn>
              <q-btn @click="equals" class="col-3 equals">=</q-btn>
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
      display: 0,
      equation: []
    }
  },
  methods: {
    allClear () {
      this.display = 0
      this.equation = []
    },
    clear () {
      if (this.display.length === 1 || this.display === 0) {
        this.display = 0
        return
      }
      this.display = this.display.substring(0, this.display.length - 1)
    },
    operator (value) {
      console.log('Operator clicked', value.target.innerText)
      this.equation.push(value.target.innerText)
      this.display += value.target.innerText
      console.log(this.equation)
    },
    number (value) {
      let numInput = value.target.innerText
      if (this.display === 0) {
        this.display = ''
      }
      this.display += numInput
      let strToNum = parseInt(numInput)
      this.equation.push(strToNum)
      console.log(this.equation)
    },
    zero () {
      if (this.display === 0) {
        this.display = 0
      } else {
        this.display += 0
        this.equation.push(0)
      }
      console.log(this.equation)
    },
    equals () {
      for (let index = 0; index < this.equation.length; index++) {
        const solve = this.equation[index]
        if (isNaN(solve)) {
          switch (solve) {
            case '+':
              this.display = this.equation[0] + this.equation[2]
              console.log('add switch', this.equation[0] + this.equation[2])
              break
            case '-':
              this.display = this.equation[0] - this.equation[2]
              // code block
              break
            case '*':
              this.display = this.equation[0] * this.equation[2]
              // code block
              break
            case '/':
              this.display = this.equation[0] / this.equation[2]
              // code block
              break
            default:
              this.display = 'error'
              // code block
          }
        }
      }
      this.equation = [this.display]
      console.log(this.equation)
    }
  }
}
</script>
