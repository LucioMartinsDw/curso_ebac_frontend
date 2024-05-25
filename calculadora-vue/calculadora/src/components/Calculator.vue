<template>
  <div class="calculator">
    <div class="display">{{ result }}</div>
    <div class="buttons">
      <button class="special" @click="clear">C</button>
      <button class="operator" @click="setOperation('/')">/</button>
      <button class="operator" @click="setOperation('*')">*</button>
      <button class="operator" @click="setOperation('-')">-</button>
      <button @click="addNumber('7')">7</button>
      <button @click="addNumber('8')">8</button>
      <button @click="addNumber('9')">9</button>
      <button class="operator" @click="setOperation('+')">+</button>
      <button @click="addNumber('4')">4</button>
      <button @click="addNumber('5')">5</button>
      <button @click="addNumber('6')">6</button>
      <button class="special" @click="equals">=</button>
      <button @click="addNumber('1')">1</button>
      <button @click="addNumber('2')">2</button>
      <button @click="addNumber('3')">3</button>
      <button @click="addNumber('0')">0</button>
    </div>
  </div>
  <div class="footer">
    Designed by Lucio de Souza Martins Web Developer Fullstack
  </div>
</template>

<script>
export default {
  data() {
    return {
      num1: "",
      num2: "",
      operation: "",
      result: "0",
    };
  },
  methods: {
    addNumber(number) {
      if (this.operation === "") {
        this.num1 += number;
        this.result = this.num1;
      } else {
        this.num2 += number;
        this.result = this.num2;
      }
    },
    setOperation(op) {
      if (this.num1 !== "" && this.num2 !== "") {
        this.equals();
      }
      this.operation = op;
    },
    equals() {
      const num1 = parseFloat(this.num1);
      const num2 = parseFloat(this.num2);

      if (isNaN(num1) || isNaN(num2)) {
        this.result = "Erro";
        return;
      }

      switch (this.operation) {
        case "+":
          this.result = num1 + num2;
          break;
        case "-":
          this.result = num1 - num2;
          break;
        case "*":
          this.result = num1 * num2;
          break;
        case "/":
          if (num2 === 0) {
            this.result = "Erro: divisão por zero";
          } else {
            this.result = num1 / num2;
          }
          break;
        default:
          this.result = "Erro";
          break;
      }

      this.num1 = this.result.toString();
      this.num2 = "";
      this.operation = "";
    },
    clear() {
      this.num1 = "";
      this.num2 = "";
      this.operation = "";
      this.result = "0";
    },
  },
};
</script>

<style scoped>
.calculator {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 300px;
  margin: 20px auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f9f9f9;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.display {
  font-size: 32px;
  font-weight: bold;
  text-align: right;
  padding: 20px;
  border: 2px solid #ccc;
  border-radius: 10px;
  margin-bottom: 20px;
  background-color: #eaeaea;
  width: 100%;
  box-sizing: border-box;
  box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.1);
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-gap: 10px;
}

button {
  width: 60px;
  height: 60px;
  border: 1px solid #ccc;
  border-radius: 10px;
  font-size: 18px;
  cursor: pointer;
  background-color: #fff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

button:active {
  box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.2);
}

button.operator {
  background-color: #b2b0ae;
  color: #fff;
}

button.special {
  background-color: #1ab0c3;
  color: #fff;
}

button:hover {
  opacity: 0.9;
}

.footer {
  margin-top: 20px;
  font-size: 12px; 
  color: #b50c0c;
  text-align: center;
}
</style>
