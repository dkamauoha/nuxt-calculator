<template>
  <section class="container">
    <div class='calculator-container'>
      <div class='calculator-display'>
        <h1 class='calculator-display-text'>{{ value }}</h1>
      </div>
      <div class='calculator-button-container'>
        <div class='calculator-button-row'>
          <b-btn class='calculator-button'></b-btn>
          <b-btn class='calculator-button' @click='clear'>C</b-btn>
          <b-btn class='calculator-button' @click='del'>DEL</b-btn>
          <b-btn class='calculator-button' @click='addExpression("/")'>/</b-btn>
        </div>
        <div class='calculator-button-row'>
          <b-btn class='calculator-button' @click='addExpression(7)'>7</b-btn>
          <b-btn class='calculator-button' @click='addExpression(8)'>8</b-btn>
          <b-btn class='calculator-button' @click='addExpression(9)'>9</b-btn>
          <b-btn class='calculator-button' @click='addExpression("*")'>x</b-btn>
        </div>
        <div class='calculator-button-row'>
          <b-btn class='calculator-button' @click='addExpression(4)'>4</b-btn>
          <b-btn class='calculator-button' @click='addExpression(5)'>5</b-btn>
          <b-btn class='calculator-button' @click='addExpression(6)'>6</b-btn>
          <b-btn class='calculator-button' @click='addExpression("-")'>-</b-btn>
        </div>
        <div class='calculator-button-row'>
          <b-btn class='calculator-button' @click='addExpression(1)'>1</b-btn>
          <b-btn class='calculator-button' @click='addExpression(2)'>2</b-btn>
          <b-btn class='calculator-button' @click='addExpression(3)'>3</b-btn>
          <b-btn class='calculator-button' @click='addExpression("+")'>+</b-btn>
        </div>
        <div class='calculator-button-row'>
          <b-btn class='calculator-button-wide' @click='addExpression(0)'>0</b-btn>
          <b-btn class='calculator-button' @click='addExpression(".")'>.</b-btn>
          <b-btn class='calculator-button' @click='getResult'>=</b-btn>
        </div>
      </div>
      <!-- <div class='calculator-button-container'>
        <div class='calculator-button-row'  v-for='(row, index) in buttons' :key='index'>
          <b-btn class='calculator-button' v-for='(val, i) in row' :key='i' :variant='val.variant'>{{val.value}}</b-btn>
        </div>
      </div> -->
    </div>
  </section>
</template>

<script>

export default {
  components: {
  },
  data: function () {
    return {
      value: 0,
      logs: [],
      buttons: [
        [
          {value: 'CE', variant: 'danger',},
          {value: 'C', variant: 'danger'},
          {value: '<-', variant: 'primary'},
          {value: '/', variant: 'primary'}
        ],
        [
          {value: '7', variant: ''},
          {value: '8', variant: ''},
          {value: '9', variant: ''},
          {value: 'x', variant: 'primary'}
        ],
        [
          {value: '4', variant: ''},
          {value: '5', variant: ''},
          {value: '6', variant: ''},
          {value: '-', variant: 'primary'}
        ],
        [
          {value: '1', variant: ''},
          {value: '2', variant: ''},
          {value: '3', variant: ''},
          {value: '+', variant: 'primary'}
        ],
        [
          {value: '+/-', variant: 'primary'},
          {value: '0', variant: ''},
          {value: '.', variant: 'primary'},
          {value: '=', variant: 'primary'}
        ],
      ]
    }
  },
  methods: {
    addExpression(e) {
      if ( Number.isInteger(this.value) )
        this.value = ''; 
      this.value += e;
    },
    getResult() {
      let log = this.value;
      this.value = eval(this.value);
      this.logs.push( log + `=${this.value}` );
    },
    clear() {
      this.value = 0;
    },
    del() {
      this.value = this.value.slice(0, -1);
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.calculator-container {
  width: 360px;
  height: 600px;
  border: 1px solid black;
  box-shadow: 1px 1px 1px 1px rgba(0,0,0,0.5);
  display: flex;
  flex-direction: column;
  align-items: center;
}
.calculator-display {
  width: 85%;
  height: 80px;
  margin-top: 40px;
  border: 1px solid black;
  display: flex;
  flex-direction: row-reverse;
  align-items: flex-end;
  overflow: hidden;
}
.calculator-display-text {
  font-size: 60px;
}
.calculator-button-container {
  margin-top: 27.5px;
  width: 85%;
  height: 420px;
  border: 1px solid black;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
}
.calculator-button-row {
  height: 18%;
  width: 95%;
  /* border: 1px solid black; */
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}
.calculator-button {
  width: 23%;
  height: 90%;
  /* border: 1px solid black; */
  box-shadow: 0.5px 0.5px 0.5px 0.5px rgba(0,0,0,0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}
.calculator-button-wide {
  width: 48%;
  height: 90%;
  /* border: 1px solid black; */
  box-shadow: 0.5px 0.5px 0.5px 0.5px rgba(0,0,0,0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
