<template>
  <div class="calculator">
    <h1 class="title">Calculadora</h1>
    <div class="input-group">
      <label for="number1">Número 1:</label>
      <input type="number" v-model="number1" id="number1" />
    </div>

    <div class="input-group">
      <label for="number2">Número 2:</label>
      <input type="number" v-model="number2" id="number2" />
    </div>

    <div class="input-group">
      <label for="operation">Operação:</label>
      <select v-model="operation" id="operation">
        <option value="+">Soma (+)</option>
        <option value="-">Subtração (-)</option>
        <option value="*">Multiplicação (*)</option>
        <option value="/">Divisão (/)</option>
      </select>
    </div>

    <div class="result">
      <strong>Resultado:</strong> {{ result }}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      number1: 0,
      number2: 0,
      operation: '+',
    };
  },
  computed: {
    result() {
      let result;
      switch (this.operation) {
        case '+':
          result = this.number1 + this.number2;
          break;
        case '-':
          result = this.number1 - this.number2;
          break;
        case '*':
          result = this.number1 * this.number2;
          break;
        case '/':
          if (this.number2 !== 0) {
            result = this.number1 / this.number2;
          } else {
            result = 'Erro: Divisão por zero';
          }
          break;
        default:
          result = 0;
      }
      return result;
    },
  },
};
</script>

<style scoped>

.calculator {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  max-width: 380px;
  margin: 40px auto;
  padding: 30px;
  background-color: #ffffff;
  border-radius: 12px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
  text-align: center;
  transition: transform 0.2s ease-in-out;
}

.calculator:hover {
  transform: translateY(-5px);
}

.title {
  font-size: 2.5rem;
  font-weight: 600;
  color: #4caf50;
  margin-bottom: 20px;
}

.input-group {
  margin-bottom: 25px;
}

.input-group label {
  display: block;
  font-size: 1.1rem;
  color: #333;
  margin-bottom: 8px;
}

input,
select {
  width: 100%;
  padding: 12px;
  font-size: 1.2rem;
  border: 2px solid #ddd;
  border-radius: 8px;
  background-color: #f7f7f7;
  box-sizing: border-box;
  transition: border-color 0.3s ease, background-color 0.3s ease;
}

input:focus,
select:focus {
  border-color: #4caf50;
  background-color: #fff;
  outline: none;
}

input[type="number"] {
  -moz-appearance: textfield;
}

input[type="number"]::-webkit-outer-spin-button,
input[type="number"]::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

select {
  padding-right: 30px;
}

.result {
  margin-top: 20px;
  font-size: 1.4rem;
  font-weight: 600;
  color: #333;
  background-color: #f1f1f1;
  padding: 12px;
  border-radius: 8px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

@media screen and (max-width: 480px) {
  .calculator {
    padding: 20px;
    max-width: 100%;
  }

  .title {
    font-size: 2rem;
  }

  input,
  select {
    font-size: 1rem;
  }

  .result {
    font-size: 1.2rem;
  }
}
</style>
