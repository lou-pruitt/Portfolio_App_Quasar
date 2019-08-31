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
              <q-btn @click="allClear" v-on:keydown.Backspace='allClear' class="col-4 ac">AC</q-btn>
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
              <q-btn @click="number" class="col-6 number">0</q-btn>
              <q-btn @click="decimal" class="col-3 decimal">.</q-btn>
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
  data: function (inputArray, input) {
    return {
      display: 0,
      equation: [],
      equationString: [],
      input: input,
      inputArray: inputArray,
      firstOperator: null,
      firstOperand: null
    }
  },
  methods: {
    allClear () {
      this.display = 0
      this.equation = []
      this.equationString = []
      console.log('allClear')
    },
    clear () {
      if (this.errorCheck() && this.equation[0] !== undefined) { // Duplicate code 1
        return
      }
      if (this.display.length === 1) {
        this.allClear()
      }
      this.equation.pop()
      this.updateDisplay()
    },
    operator (value) {
      if (this.errorCheck() && this.equation[0] !== undefined) { // Duplicate code 1
        return
      }
      if (this.equation.length < 1) {
        return
      }
      if (isNaN(value)) {
        value = value.target.innerText
        this.input = value
      }
      if (this.isLastInputNum(this.equation)) {
        this.equation.push(value)
      } else {
        this.replaceLastInput(this.equation, this.input)
      }
      this.updateDisplay()
      console.log('operator executed')
    },
    replaceLastInput (equation, value) {
      equation[equation.length - 1] = value
      console.log('replaceLastInput executed')
    },
    number (value) {
      if (this.errorCheck() && this.equation[0] !== undefined) { // Duplicate code 1
        return
      }
      this.input = value.target.innerText
      if (typeof this.input !== 'string') {
        this.input = value.target.innerText
        this.input = value
      }
      if (this.isLastInputNum(this.equation) || this.equation[this.equation.length - 1] === '.') {
        this.concatLastInput(this.equation, this.input)
      } else {
        this.equation.push(this.input)
      }
      this.updateDisplay()
    },
    decimal (value) {
      if (this.errorCheck() && this.equation[0] !== undefined) { // Duplicate code 1
        return
      }
      this.input = value.target.innerText
      console.log('decimal method')
      if (this.equation[0] === undefined) {
        this.equation[0] = 0
      }
      if (this.hasDecimal(this.equation[this.equation.length - 1])) {
        return
      }
      if (typeof this.input !== 'string') {
        this.input = value.target.innerText
      }
      if (this.isLastInputNum(this.equation)) {
        this.concatLastInput(this.equation, this.input)
      } else {
        this.equation.push(this.input)
      }
      this.updateDisplay()
    },
    hasDecimal (str) {
      console.log('hasDecimal executed')
      return str && str.toString().indexOf('.') > -1
    },
    equals () {
      if (this.errorCheck() && this.equation[0] !== undefined) { // Duplicate code 1
        return
      }
      var operatorIndex = 1
      if (this.equation.length === 1 && this.firstOperand && this.firstOperator) {
        this.equation[0] = this.doMath(this.equation[0], this.firstOperand, this.firstOperator)
      }
      while (this.equation.length > 2) {
        var input = this.equation[operatorIndex]
        var input2 = this.equation[operatorIndex + 1]
        if (isNaN(input) && input2) {
          var operand1 = Number(this.equation[operatorIndex - 1])
          var operand2 = Number(this.equation[operatorIndex + 1])
          this.firstOperator = input
          this.firstOperand = operand2
          this.equation.splice(0, operatorIndex + 2, this.doMath(operand1, operand2, input))
        }
      }
      if (this.equation.length === 2) {
        this.firstOperator = this.firstOperator ? this.firstOperator : this.equation[operatorIndex]
        operand1 = Number(this.equation[0])
        operand2 = Number(this.equation[0])
        this.equation.splice(0, operatorIndex + 1, this.doMath(operand1, operand2, this.firstOperator))
      }
      this.updateDisplay()
      console.log('equals executed')
      this.display = [this.equation]
      console.log(this.equation)
      if (!isFinite(this.equation[0])) {
        this.error()
        console.log('To infinity, ...and BEYOND!')
      } else if (this.equation[0] === undefined) {
        this.allClear()
      }
    },
    doMath (x, y, operator) {
      console.log('doMath executed')
      switch (operator) {
        case '+':
          return x + y
        case '-':
          return x - y
        case '/':
          return x / y
        case 'x':
        case '*':
          return x * y
        default:
          return 'invalid operator'
      }
    },
    isLastInputNum () {
      return !isNaN(this.equation[this.equation.length - 1])
    },
    concatLastInput () {
      this.equation[this.equation.length - 1] += this.input
    },
    updateDisplay () {
      let result = this.equation.join(' ')
      if (this.equation.length === 0) {
        result = '0'
      }
      this.display = result
      console.log(this.equation)
    },
    error () {
      this.display = 'Error'
    },
    errorCheck () {
      console.log('equation[0] value: ', this.equation[0])
      return !isFinite(this.equation[0])
    }
  },
  mounted () {
    window.addEventListener('keypress', function (e) {
      var key = e.key
      console.log(String.fromCharCode(key))
    })
  }
}
</script>
