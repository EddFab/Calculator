<template>
<div class="container-fluid">
  <div class="row">

    <!--SPACER-->
    <div class="col-5"></div>

    <!--MIDDLE DIV-->
    <div class="col-2 mt-5">

      <h1>Calculator</h1>

      <div class="row">
        <div class="col-12 display-box"></div>
      </div>

      <div class="row first-row">
        <button type="button" class="col-3">AC</button>
        <button type="button" class="col-3">+/-</button>
        <button type="button" class="col-3">%</button>
        <button type="button" class="col-3">&#247;</button>
      </div>
      <div class="row second-row">
        <button type="button" class="col-3">7</button>
        <button type="button" class="col-3">8</button>
        <button type="button" class="col-3">9</button>
        <button type="button" class="col-3">x</button>
      </div>
      <div class="row third-row">
        <button type="button" class="col-3">4</button>
        <button type="button" class="col-3">5</button>
        <button type="button" class="col-3">6</button>
        <button type="button" class="col-3">-</button>
      </div>
      <div class="row fourth-row">
        <button type="button" class="col-3">1</button>
        <button type="button" class="col-3">2</button>
        <button type="button" class="col-3">3</button>
        <button type="button" class="col-3">+</button>
      </div>
      <div class="row sixth-row">
        <button type="button" class="col-6">0</button>
        <button type="button" class="col-3">.</button>
        <button type="button" class="col-3">=</button>
      </div>

    </div>

    <!--SPACER-->
    <div class="col-5"></div>

  </div>
</div>
</template>

<script>
export default {}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.display-box {
  background-color: #333;
  min-height: 100px;
}

.h100 {
  height: 100%;
}

button {
  background-color: #cecfd2;
  color:#fff;
  padding: 15px 10px;
  border-style: solid;
  border-color: #333;
  border-width: thin;
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
