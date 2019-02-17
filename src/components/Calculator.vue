<template>
  <div class="calculator">
    <!-- result -->
    <div class="result">{{current || 0}}</div>
    
    <!-- row one -->
    <div class="btn" @click="clear">AC</div>
    <div class="btn" @click="sign">+/-</div>
    <div class="btn" @click="percent">%</div>
    <div class="btn operator" @click="divide">÷</div>

    <!-- row two -->
    <div class="btn" @click="append('7')">7</div>
    <div class="btn" @click="append('8')">8</div>
    <div class="btn" @click="append('9')">9</div>
    <div class="btn operator" @click="multi">x</div>

    <!-- row three -->
    <div class="btn" @click="append('4')">4</div>
    <div class="btn" @click="append('5')">5</div>
    <div class="btn" @click="append('6')">6</div>
    <div class="btn operator" @click="minus">-</div>

    <!-- row four -->
    <div class="btn" @click="append('1')">1</div>
    <div class="btn" @click="append('2')">2</div>
    <div class="btn" @click="append('3')">3</div>
    <div class="btn operator" @click="plus">+</div>

    <!-- row four -->
    <div class="btn zero" @click="append('0')">0</div>
    <div class="btn" @click="dot">.</div>
    <div class="btn operator">=</div>

  </div>
</template>

<script>
export default {
  data() {
    return {
      previous: null,
      current: '',
      operator: null,
      operatorClicked: false
    }
  },
  methods: {
    clear() {
      this.current = ''
    },
    // `${}` is a string of
    sign() {
      this.current = this.current.charAt(0) == '-' ?
        this.current.slice(1): `-${this.current}`;
    },
    percent() {
      this.current = `${parseFloat(this.current) / 100}`
    },
    append(number) {
      if(this.operatorClicked) {
        this.current = '';
        this.operatorClicked = false;
      }
      this.current = `${this.current}${number}`
    },
    dot() {
      if(this.current.indexOf('.') === -1) {
        this.append('.');
        // this.current = `${this.current}${'.'}`
      }
    },
    setPrevious() {
      this.previous = this.current;
      this.operatorClicked = true;
    },
    divide() {
      this.operator = (a, b) => a / b;
      this.setPrevious();
    },
    multi() {
      this.operator = (a, b) => a * b;
      this.setPrevious();
    },
    minus() {
      this.operator = (a, b) => a - b;
      this.setPrevious();
    },
    plus() {
      this.operator = (a, b) => a + b;
      this.setPrevious();
    },
  },
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
