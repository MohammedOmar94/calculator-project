<template>
  <div>
    <h1>{{ title }}</h1>
    <h2></h2>
  <div>
  <div class="row">
    <input v-model="calculation" type="text" class="col-lg-7 offset-md-1">
  </div>
  <div class="row">
    <p class="col-sm-1 offset-md-2" @click="enterNumber(1)">1</p>
    <p class="col-sm-1 other-buttons" @click="enterNumber(2)">2</p>
    <p class="col-sm-1 other-buttons" @click="enterNumber(3)">3</p>
    <p class="col-sm-1 other-buttons" @click="subtract">-</p>
  </div>
  <div class="row">
    <p class="col-sm-1 offset-md-2" @click="enterNumber(4)">4</p>
    <p class="col-sm-1 other-buttons" @click="enterNumber(5)">5</p>
    <p class="col-sm-1 other-buttons" @click="enterNumber(6)">6</p>
    <p class="col-sm-1 other-buttons" @click="add">+</p>
  </div>
  <div class="row">
    <p class="col-sm-1 offset-md-2" @click="enterNumber(7)">7</p>
    <p class="col-sm-1 other-buttons" @click="enterNumber(8)">8</p>
    <p class="col-sm-1 other-buttons" @click="enterNumber(9)">9</p>
    <p class="col-sm-1 other-buttons" @click="divide">/</p>
  </div>
  <div class="row">
    <p class="col-sm-1 offset-md-2" @click="multiply">x</p>
    <p class="col-sm-1 other-buttons" @click="displayResult">=</p>
  </div>
  </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      title: 'Calculator.vue',
      calculation: '',
      previousValue: '',
      currentValue: '',
      newValue: '',
      operative: ''
    }
  },
  methods: {
    enterNumber (number) {
        // Resets display when an operator is used.
      if (this.operative !== '') {
        this.currentValue = this.currentValue + number
        this.determineOperation()
      }
        // Displays number being typed.
      this.calculation = this.calculation + number
    },
    determineOperation () {
      switch (this.operative) {
        case '+':
          this.newValue = parseInt(this.previousValue) + parseInt(this.currentValue)
          break
        case '-':
          break
        case '/':
          break
        case 'x':
          break
      }
    },
    add () {
      // Every time the + operator is selected, store the previous value.
      this.previousValue = this.calculation

      // Update the display
      this.calculation = this.calculation + '+'
      this.operative = '+'
    },
    subtract () {
      // this.calculation = this.calculation + '-'
      this.operative = '-'
      this.newValue = parseInt(this.previousValue) - parseInt(this.calculation)
    },
    divide () {
      // this.calculation = this.calculation + '/'
      this.operative = '/'
      this.newValue = parseInt(this.previousValue) / parseInt(this.calculation)
    },
    multiply () {
      // this.calculation = this.calculation + '*'
      this.operative = '*'
      this.newValue = parseInt(this.previousValue) * parseInt(this.calculation)
    },
    displayResult () {
      this.calculation = this.newValue
      this.previousValue = ''
      this.currentValue = ''
      this.newValue = ''
      this.operative = ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input {
  margin-bottom:20px;
  font-size: 24px;
  font-weight: bold;
  left:12px;
}
h1, h2 {
  font-weight: normal;
  margin-bottom:80px;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
p {
  border: 0.5px solid;
  padding: 15px;
  font-size:18px;
}
p:hover {
  background:#42b983;
  color:white;
  font-weight: bold;
  border: none;
  padding: 15px;
  font-size:18px;
}
.other-buttons{
  margin-left: 10px;
}
</style>
