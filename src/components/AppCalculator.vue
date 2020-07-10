<template>
  <div>
    <h1 class="title">Vue Calculator</h1>
    <div class="wrapper">
      <div class="display">{{ current || 0 }}</div>
      <div @click="divide" class="btn operator">÷</div>
      <div @click="times" class="btn operator">x</div>
      <div @click="clear" class="clear btn operator">C</div>
      <div @click="append('7')" class="btn">7</div>
      <div @click="append('8')" class="btn">8</div>
      <div @click="append('9')" class="btn">9</div>
      <div @click="minus" class="btn operator">-</div>
      <div @click="append('4')" class="btn">4</div>
      <div @click="append('5')" class="btn">5</div>
      <div @click="append('6')" class="btn">6</div>
      <div @click="add" class="btn operator">+</div>
      <div @click="append('1')" class="btn">1</div>
      <div @click="append('2')" class="btn">2</div>
      <div @click="append('3')" class="btn">3</div>
      <div @click="percent" class="btn operator">%</div>
      <div @click="append('0')" class="zero btn">0</div>
      <div @click="dot" class="btn">.</div>
      <div @click="equal" class="btn equals">=</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AppCalculator',
  data() {
    return {
      current: '',
      previous: null,
      operator: null,
      operatorClicked: false
    }
  },
  methods: {
    clear() {
      this.current = ''
    },
    percent() {
      this.current = `${parseFloat(this.current) / 100}`
    },
    append(number) {
      if (this.operatorClicked) {
        this.current = ''
        this.operatorClicked = false
      }
      this.current = `${this.current}${number}`
    },
    dot() {
      if (this.current.indexOf('.') === -1) {
        this.append('.')
      }
    },
    setOperator() {
      this.operatorClicked = true
      this.previous = this.current
    },
    divide() {
      this.operator = (a, b) => a / b
      this.setOperator()
    },
    times() {
      this.operator = (a, b) => a * b
      this.setOperator()
    },
    minus() {
      this.operator = (a, b) => a - b
      this.setOperator()
    },
    add() {
      this.operator = (a, b) => a + b
      this.setOperator()
    },
    equal() {
      this.current = this.operator(
        parseFloat(this.previous),
        parseFloat(this.current)
      )
      this.previous = null
    }
  }
}
</script>

<style scoped>
.title {
  font-weight: bold;
  font-size: 1.5rem;
  text-align: center;
  margin-bottom: 1.5rem;
  color: white;
}
.wrapper {
  font-size: 1.5rem;
  max-width: 30rem;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(3rem, auto);
}

.display {
  grid-column: 1 / 5;
  background: #333;
  color: white;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  text-align: right;
  padding: 2rem 1rem;
}

.clear {
  grid-column: 3 / 5;
}
.zero {
  grid-column: 1 / 3;
}

.btn {
  background-color: #ccc;
  border: 0.2px solid rgb(199, 199, 199);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1rem 0;
  cursor: pointer;
}

.btn:hover {
  background-color: rgb(168, 167, 167);
}

.equals {
  background: orange;
}
.equals:hover {
  background: rgb(196, 128, 2);
}

.operator {
  background: rgb(187, 187, 187);
}
</style>
