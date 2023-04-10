<script>
  export default {
    data() {
      return {
        num1: 0,
        num2: 0,
        operator: 'add',
        result: null
      }
    },
    methods: {
      calculate() {
        switch(this.operator) {
          case "add":
            this.result = this.num1 + this.num2
            break
          case "subtract":
            this.result = this.num1 - this.num2
            break
          case "multiplie":
            this.result = this.num1 * this.num2
            break
          case "divide":
            this.result = (this.num1 / this.num2).toFixed(4)
            break
        }
      }
    }
  }
</script>

<template>
  <main>
    <h1>Calculadora</h1>
    <form @submit.prevent="calculate">
      <input type="number" v-model="num1">
      <select v-model="operator">
        <option value="add">+</option>
        <option value="subtract">-</option>
        <option value="multiplie">x</option>
        <option value="divide">/</option>
      </select>
      <input type="number" v-model="num2">
      <button type="submit">Calcular</button>
    </form>
    <div v-if="result !== null">
      <p id="res">Resultado: <strong>{{ result }}</strong></p>
    </div>
  </main>
</template>

<style scoped>
  main {
    margin: 0 auto;
    height: 100vh;
    display: flex;
    flex-direction: column;
    gap: 2em;
    justify-content: center;
    align-items: center;
  }

  form > * {
    margin-inline: 8px;
  }

  input, select, button {
    padding: 0.5em 0.75em;
    border-radius: 0.25em;
  }

  input[type=number] {
    width: 100px;
  }

  button[type=submit] {
    cursor: pointer;
  }

  #res {
    font-size: 1.35em;
  }

  @media (max-width: 767px) {
    form {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }
  }
</style>
