<template>
  <div id="app">
    <h1>Calculadora Vue</h1>
    <div class="calculadora">
      <input type="text" v-model="pantalla" readonly>
      <div class="botones">
        <button v-for="n in 9" :key="n" @click="agregarNumero(n)">{{ n }}</button>
        <button @click="agregarNumero(0)">0</button>
        <button @click="agregarOperador('+')">+</button>
        <button @click="agregarOperador('-')">-</button>
        <button @click="agregarOperador('*')">*</button>
        <button @click="agregarOperador('/')">/</button>
        <button @click="calcular">=</button>
        <button @click="limpiar">C</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      pantalla: ''
    }
  },
  methods: {
    agregarNumero(numero) {
      this.pantalla += numero.toString()
    },
    agregarOperador(operador) {
      this.pantalla += ' ' + operador + ' '
    },
    calcular() {
      try {
        this.pantalla = eval(this.pantalla).toString()
      } catch (e) {
        this.pantalla = 'Error'
      }
    },
    limpiar() {
      this.pantalla = ''
    }
  }
}
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  margin-top: 50px;
}

.calculadora {
  width: 200px;
  margin: 0 auto;
}

input {
  width: 100%;
  margin-bottom: 10px;
  padding: 5px;
  font-size: 18px;
}

.botones {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 5px;
}

button {
  padding: 10px;
  font-size: 16px;
  cursor: pointer;
}
</style>
