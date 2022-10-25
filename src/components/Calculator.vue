<script>
export default {
  name: "PlainCalculator",
  data() {
    return {
      result: "0",
      operation: "",
      firstNumber: "",
      secondNumber: "",
      operatorExist: false,
      operator: ""
    }
  },
  methods: {
    addToDisplay(value){

      if (this.operation === "0"){
        return this.operation = value
      }

      this.operation += value

      !this.operatorExist ? this.firstNumber += value : null
      this.operatorExist ? this.secondNumber += value : null
    },

    addOperatorToDisplay(value){
      if (!this.operatorExist){
        this.operation += ` ${value} `

        this.operator = value

        this.operatorExist = true
      }
    },

    deleteAll(){
      this.operation = ""
      this.operatorExist = false
      this.operator = ""
      this.result = "0"
      this.firstNumber = ""
      this.secondNumber = ""
    },

    delete(){
      if (this.operation.substr(this.operation.length-1, this.operation.length) === " "){
        this.operatorExist = false
        return this.operation = this.operation.substr(0, this.operation.length-3)
      }
      this.operation = this.operation.substr(0, this.operation.length-1)

      this.operatorExist ? this.secondNumber += this.secondNumber.substr(0, this.secondNumber.length-1) : null
    },

    calculate(){
      const numberOne = parseFloat(this.firstNumber)
      const numberTwo = parseFloat(this.secondNumber)

      switch (this.operator) {
        case "+":
          this.result = numberOne + numberTwo
              break
        case "-":
          this.result = numberOne - numberTwo
              break
        case "x":
          this.result = numberOne * numberTwo
              break
        case "/":
          this.result = numberOne / numberTwo
              break
        default:
            this.result = this.operation
      }
    }
  }
}
</script>

<template>
  <div class="main-container">
    <div class="calculator-container">
      <div class="display">
        <div class="result">{{ result }}</div>
        <div class="operation">{{ operation }}</div>
      </div>
      <div class="keyboard">
        <button v-on:click="this.deleteAll" id="delete-all" class="button operator">CA</button>
        <button v-on:click="this.delete" id="delete" class="button operator">C</button>
        <button v-on:click="this.addToDisplay('7')" id="seven" class="button number">7</button>
        <button v-on:click="this.addToDisplay('8')" id="eight" class="button number">8</button>
        <button v-on:click="this.addToDisplay('9')" id="nine" class="button number">9</button>
        <button v-on:click="this.addOperatorToDisplay('-')" id="less" class="button operator">-</button>
        <button v-on:click="this.addOperatorToDisplay('/')" id="divide" class="button operator">/</button>
        <button v-on:click="this.addToDisplay('4')" id="four" class="button number">4</button>
        <button v-on:click="this.addToDisplay('5')" id="five" class="button number">5</button>
        <button v-on:click="this.addToDisplay('6')" id="six" class="button number">6</button>
        <button v-on:click="this.addOperatorToDisplay('+')" id="plus" class="button operator">+</button>
        <button v-on:click="this.addOperatorToDisplay('x')" id="multiply" class="button operator">x</button>
        <button v-on:click="this.addToDisplay('1')" id="one" class="button number">1</button>
        <button v-on:click="this.addToDisplay('2')" id="two" class="button number">2</button>
        <button v-on:click="this.addToDisplay('3')" id="three" class="button number">3</button>
        <button disabled v-on:click="this.addOperatorToDisplay('%')" id="percentage" class="button operator">%</button>
        <button v-on:click="this.addToDisplay('0')" id="zero" class="button number">0</button>
        <button v-on:click="this.addToDisplay('.')" id="point" class="button number">.</button>
        <button v-on:click="this.calculate" id="equal" class="button operator">=</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
  .display{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: end;
    height: 142px;
    padding-right: 20px;
  }

  .result{
    font-size: 50px;
  }

  .operation{
    font-size: 18px;
    height: 10px;
  }

  .keyboard{
    display: grid;
    grid-template-columns: 20% 20% 20% 20% 20%;
    grid-template-rows: 20% 20% 20% 20% 20%;
  }

  .button{
    display: flex;
    align-items: center;
    justify-content: center;
    width: 50px;
    height: 50px;
    margin: 5px;
    cursor: pointer;
    background-color: transparent;
    color: aliceblue;
    border: 0;
    border-radius: 14px;
    transition: .3s ease-in-out;
  }

  .button:hover{
    background-color: #00414b;
    transition: .3s ease-in-out;
  }

  .number{
    width: 48px;
    height: 48px;
    border: #006070 2px solid;
  }

  .operator{
    background-color: rgb(12, 157, 182);
    transition: .3s ease-in-out;
  }

  .operator:hover{
    background-color: #006070;
    transition: .3s ease-in-out;
  }

  #delete-all{
    width: 110px;
    grid-column: 1/3;
  }

  #delete{
    width: 170px;
    grid-column: 3/6;
  }

  #plus{
    height: 110px;
    grid-column: 4;
    grid-row: 3/5;
  }

  #zero{
    width: 110px;
    grid-column: 1/3;
  }

  #equal{
    width: 110px;
    grid-column: 4/6;
  }

  .main-container{
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background: linear-gradient(138deg, rgba(1,185,217,1) 0%, rgba(0,98,117,1) 100%);
  }

  .calculator-container{
    height: 450px;
    width: 300px;
    background-color: #005B68;
    border-radius: 17px;
  }
</style>