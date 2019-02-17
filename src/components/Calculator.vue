<template>
  <div class="calculator">
    <!-- result -->
    <div class="result">7902345</div>
    
    <!-- row one -->
    <div class="btn">AC</div>
    <div class="btn">+/-</div>
    <div class="btn">%</div>
    <div class="btn operator">÷</div>

    <!-- row two -->
    <div class="btn">7</div>
    <div class="btn">8</div>
    <div class="btn">9</div>
    <div class="btn operator">x</div>

    <!-- row three -->
    <div class="btn">4</div>
    <div class="btn">5</div>
    <div class="btn">6</div>
    <div class="btn operator">-</div>

    <!-- row four -->
    <div class="btn">1</div>
    <div class="btn">2</div>
    <div class="btn">3</div>
    <div class="btn operator">+</div>

    <!-- row four -->
    <div class="btn zero">0</div>
    <div class="btn">.</div>
    <div class="btn operator">=</div>

  </div>
</template>

<script>
export default {
}
</script>

<style scoped>
.calculator {
  margin: 0 auto;
  width: 400px;
  font-size: 40px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}
.result {
  grid-column: 1 / 5;
  background-color: #333;
  color: #fff
}
/* to make two columns */
.zero {
  grid-column: 1 / 3;
}
.btn {
  background-color: #f2f2f2;
  border: 1px solid #999;
}
.operator {
  background-color: orange;
}
</style>
