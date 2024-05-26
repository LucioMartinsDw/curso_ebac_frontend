<template>
  <div class="calculator">
    <div class="input-fields">
      <input
        type="number"
        v-model="num1"
        placeholder="Primeiro número"
        @keyup="calculate"
      />
      <select v-model="operation">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select>
      <input
        type="number"
        v-model="num2"
        placeholder="Segundo número"
        @keyup="calculate"
      />
    </div>
    <div class="result">
      <p>Resultado: {{ result }}</p>
    </div>
    <button @click="reset">Limpar</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      num1: 0,
      num2: 0,
      operation: "+",
      result: 0,
    };
  },
  methods: {
    calculate() {
      switch (this.operation) {
        case "+":
          this.result = this.num1 + this.num2;
          break;
        case "-":
          this.result = this.num1 - this.num2;
          break;
        case "*":
          this.result = this.num1 * this.num2;
          break;
        case "/":
          if (this.num2 === 0) {
            this.result = "Divisão por zero!";
          } else {
            this.result = this.num1 / this.num2;
          }
          break;
      }
    },
    reset() {
      this.num1 = 0;
      this.num2 = 0;
      this.operation = "+";
      this.result = 0;
    },
  },
};
</script>

<style scoped>
.calculator {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 300px;
  margin: auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.2);
  background-color: #f8f9fa;
}

.input-fields {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.input-fields input[type="number"],
.input-fields select {
  width: 100%;
  padding: 10px;
  margin: 10px 0;
  border: 1px solid #ccc;
  border-radius: 3px;
}

.result p {
  font-size: 20px;
  font-weight: bold;
  color: #333;
}

.calculator button {
  background-color: #e91e63; 
  color: #fff;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 10px; 
}
</style>
