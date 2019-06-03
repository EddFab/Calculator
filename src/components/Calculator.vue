<template>
<div class="container-fluid">
  <div class="row">

    <!--SPACER-->
    <div class="col-1 col-sm-3 col-md-4 col-lg-5"></div>

    <!--MIDDLE DIV-->
    <div class="col-10 col-sm-6 col-md-4 col-lg-2" style="margin-top:100px;">


      <div class="row">
        <h1 class="col-12 text-center p-0 m-0 mb-3">CALCULATOR</h1>
        <div class="col-12 display-box text-right">
          <h2 class="">{{current || '0'}}</h2>
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
    <div class="col-1 col-sm-3 col-md-4 col-lg-5"></div>

  </div>
</div>
</template>

<script>
export default {
  data() {
    return {
      signal: null,
      previous: null,
      current: '',
      operator: null,
      operatorClicked: false,
    }
  },
  methods: {
    clear() {
      this.current = '';
    },
    sign() {
      //IF THE USER PRESSES +/- SYMBOL WHILE VALUE IS 0
      if ((this.current === '') || (this.current === '0')) {
        this.current = '';
      } else {
        this.current *= -1;
      }
    },
    percent() {
      this.current = `${parseFloat(this.current)/100}`;
    },
    append(number) {
      //IF THE VALUE IS ALREADY 0 && THE USER IS ADDING ZEROES
      if (this.current == 0 || !this.current) {
        this.current = '';
      }
      //IF ANY OPERATOR BUTTON HAS BEEN CLICKED
      else if (this.operatorClicked) {
        this.current = '';
        this.operatorClicked = false;
      }
      this.current = `${this.current}${number}`;

    },
    dot() {
      if (this.current.indexOf('.') === -1) {
        this.append('.');
      }
    },
    setPrevious() {
      this.previous = this.current;
      this.operatorClicked = true;
      this.current = this.signal;
    },
    divide() {
      this.signal = '/';
      this.setPrevious();
      this.operator = (a, b) => b / a;
    },
    times() {
      this.signal = 'x';
      this.setPrevious();
      this.operator = (a, b) => b * a;
    },
    minus() {
      this.signal = '-';
      this.setPrevious();
      this.operator = (a, b) => b - a;
    },
    add() {
      this.signal = '+';
      this.setPrevious();
      this.operator = (a, b) => b + a;
    },
    equal() {
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
  height: 75px;
}

.h100 {
  height: 100%;
}

h1 {
  font-family: 'Faster One', cursive;
  color: #333;
  font-size: 2em;
}

h2 {
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
