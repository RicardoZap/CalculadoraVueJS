<template>
<div class="calculator bg-green-500">

  <!-- the input -->
  <div class="bg-white pt-16 p-5 pb-0 text-black text-right text-3xl">{{ getResult }} </div>

  <!-- the buttons -->
  <div class="calculator-buttons">
    <button class="calc-button is-clear bg-red-400" @click="clickAC()">C</button>
    <button class="calc-button bg-red-600" @click="click('/')">/</button>

    <button class="calc-button bg-red-600" @click="click('7')">7</button>
    <button class="calc-button bg-red-600" @click="click('8')">8</button>
    <button class="calc-button bg-red-600" @click="click('9')">9</button>
    <button class="calc-button bg-red-600" @click="click('x')">*</button>

    <button class="calc-button bg-red-600" @click="click('4')">4</button>
    <button class="calc-button bg-red-600" @click="click('5')">5</button>
    <button class="calc-button bg-red-600" @click="click('6')">6</button>
    <button class="calc-button bg-red-600" @click="click('-')">-</button>

    <button class="calc-button bg-red-600" @click="click('1')">1</button>
    <button class="calc-button bg-red-600" @click="click('2')">2</button>
    <button class="calc-button bg-red-600" @click="click('3')">3</button>
    <button class="calc-button bg-red-600" @click="click('+')">+</button>

    <button class="calc-button is-zero bg-red-600" @click="click('0')">0</button>
    <button class="calc-button is-equals bg-red-600" @click="clickResult()">=</button>
  </div>
  
</div>  
</template>

<script>

export default {
  
  data () {
    return{
      getOperation: '',
      getResult: '0',
    }
  },

  methods: {
    clickAC(){
      this.getResult = '0';
    },
    click(num){
      if(this.getResult == '0'){
        this.getResult = num;
      }else{
        this.getResult += num;
      }
    },
    clickResult(){
      let operation = this.getResult;
      this.getOperation = operation;

      operation = operation.replace('x', '*');
      operation = operation.replace('/', '/');
      this.getResult = eval(operation);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

* {
  box-sizing: border-box;
}

.calculator input,
.calc-button   {
  font-family: 'Space Mono';
}

/* add some spacing */
body          {
  background: #F6F6F6;
  padding-bottom: 30px;
  padding-top: 30px;  
}

/* limit the width and center */
.calculator   {
  max-width: 400px;
  margin: 0 auto;
  border: 2px solid #111;
  border-radius: 5px;
}

.calculator input   {
  /* reset basic form styles */
  border: none;
  box-shadow: none;
  outline: none;

  padding: 20px 10px;
  width: 100%;
  border-bottom: 2px solid #111;
  color: #333;
  text-align: right;
  font-size: 40px;
  border-radius: 0;
}

.calc-button  {
  border: 1px solid #111; /* black border */
  padding: 20px;
  color: #EEE; /* white text */
  border-radius: 5px; /* rounded corners */
  font-size: 22px; /* larger fonts */
  cursor: pointer; /* make it look clickable */
}

.calculator-buttons {
  /* small spacing within our container */
  padding: 20px;

  /* the grid stuff! */
  display: grid;

  /* create 4 columns */
  grid-template-columns: 1fr 1fr 1fr 1fr;

  /* add the grid gap */
  grid-gap: 15px;
}

/* span across 3 columns */
.is-zero,
.is-clear   {
  grid-column: span 3;
}

/* go blue */
.is-clear   {
  background: #3572DB;
}

.is-equals {
  background: #28D060;
}
</style>
