<template>
<div class="container-fluid">
  <div class="row">

    <!--SPACER-->
    <div class="col-5"></div>

    <!--MIDDLE DIV-->
    <div class="col-2 mt-5">

      <h1>Calculator</h1>

      <div class="row">
        <div class="col-12 display-box text-right">
          <h2 class="">{{current || '0' }}</h2>
        </div>
      </div>

      <div class="row first-row">
        <button @click="clear" type="button" class="col-3">AC</button>
        <button @click="sign" type="button" class="col-3">+/-</button>
        <button @click="percent" type="button" class="col-3">%</button>
        <button @click="divide" type="button" class="col-3">&#247;</button>
      </div>
      <div class="row second-row">
        <button @click="append('7')" type="button" class="col-3">7</button>
        <button @click="append('8')" type="button" class="col-3">8</button>
        <button @click="append('9')" type="button" class="col-3">9</button>
        <button @click="times" type="button" class="col-3">x</button>
      </div>
      <div class="row third-row">
        <button @click="append('4')" type="button" class="col-3">4</button>
        <button @click="append('5')" type="button" class="col-3">5</button>
        <button @click="append('6')" type="button" class="col-3">6</button>
        <button @click="minus" type="button" class="col-3">-</button>
      </div>
      <div class="row fourth-row">
        <button @click="append('1')" type="button" class="col-3">1</button>
        <button @click="append('2')" type="button" class="col-3">2</button>
        <button @click="append('3')" type="button" class="col-3">3</button>
        <button @click="add" type="button" class="col-3">+</button>
      </div>
      <div class="row sixth-row">
        <button @click="append('0')" type="button" class="col-6">0</button>
        <button @click="dot" type="button" class="col-3">.</button>
        <button @click="equal" type="button" class="col-3">=</button>
      </div>

    </div>

    <!--SPACER-->
    <div class="col-5"></div>

  </div>
</div>
</template>

<script>
export default {
  data() {
    return {
      previous:null,
      current: '',
      operator:null,
      operatorClicked:false,
    }
  },
  methods:{
    clear(){
      this.current = '';
    },
    sign(){
      this.current = this.current.charAt(0) === '-' ? this.current.slice(1) : `-${this.current}`;
    },
    percent(){
      this.current = `${parseFloat(this.current) / 100}`;
    },
    append(number){
      if(this.operatorClicked){
        this.current = '';
        this.operatorClicked = false;
      }
      this.current = `${this.current}${number}`;
    },
    dot(){
      if (this.current.indexOf('.') === -1){
        this.append('.');
      }
    },
    setPrevious(){
      this.previous = this.current;
      this.operatorClicked = true;
    },
    divide(){
      this.operator = (a, b) => a / b;
      this.setPrevious();
    },
    times(){
      this.operator = (a, b) => a * b;
      this.setPrevious();
    },
    minus(){
      this.operator = (a, b) => a - b;
      this.setPrevious();
    },
    add(){
      this.operator = (a, b) => a + b;
      this.setPrevious();
    },
    equal(){
      this.current = `${this.operator(
        parseFloat(this.current),
        parseFloat(this.previous)
      )}`;
      this.previous = null;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.display-box {
  background-color: #333;
  padding: 20px 10px;
}

.h100 {
  height: 100%;
}
h1 {
  font-family: 'Cabin Sketch', cursive;
  color: #333;
}
h2{
  color: #fff;
  margin-bottom: 0;
}

button {
  background-color: #cecfd2;
  color: #fff;
  padding: 15px 10px;
  border-style: solid;
  border-color: #333;
  border-width: thin;
  font-family: 'Montserrat', sans-serif;
}

.second-row button {
  background-color: #B9BABD;
}

.third-row button {
  background-color: #A4A5A8;
}

.fourth-row button {
  background-color: #909093;
}

.fifth-row button {
  background-color: #7B7C7E;
}

.sixth-row button {
  background-color: #676769;
}
</style>
