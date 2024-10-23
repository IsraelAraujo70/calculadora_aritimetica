<script setup>
import { reactive } from 'vue';

const estado = reactive({
  primeiro: 0,
  segundo: 0,
  resultado: 0
})

function somar(){
  estado.resultado = Number(estado.primeiro) + Number(estado.segundo)
  return estado.resultado
}
function subtracao(){
  estado.resultado = Number(estado.primeiro) - Number(estado.segundo)
  return estado.resultado
}
function multiplicar(){
  estado.resultado = Number(estado.primeiro) * Number(estado.segundo)
  return estado.resultado
}
function dividir(){
  if (estado.segundo !== 0) {
    estado.resultado = Number(estado.primeiro) / Number(estado.segundo)
  } else {
    estado.resultado = 'Erro: Divisão por zero'
  }
  return estado.resultado
}
function exponenciacao(){
  estado.resultado = Math.pow(Number(estado.primeiro), Number(estado.segundo))
  return estado.resultado
}
function raiz(){
  if (estado.primeiro >= 0) {
    estado.resultado = Math.sqrt(Number(estado.primeiro))
  } else {
    estado.resultado = 'Erro: Raiz negativa'
  }
  return estado.resultado
}
function realizarOperacao(operacao) {
  switch (operacao) {
    case 'somar':
      somar();
      break;
    case 'subtracao':
      subtracao();
      break;
    case 'multiplicar':
      multiplicar();
      break;
    case 'dividir':
      dividir();
      break;
    case 'exponenciacao':
      exponenciacao();
      break;
    case 'raiz':
      raiz();
      break;
  }
}
</script>

<template>
  <body>  
    <div class="container">
      <h1 class="mt-5 mb-5">Calculadora Aritimética</h1>
      <h2>Insira os números:</h2>
      <div class="numeros">
        <input type="number" @keyup="evento => estado.primeiro = evento.target.value">
        <input type="number" @keyup="evento => estado.segundo = evento.target.value">
      </div>
      <div class="operadores">
        <select @change="evento => realizarOperacao(evento.target.value)" class="operador-seletor">
          <option value="somar">Soma</option>
          <option value="subtracao">Subtração</option>
          <option value="multiplicar">Multiplicação</option>
          <option value="dividir">Divisão</option>
          <option value="exponenciacao">Exponenciação</option>
          <option value="raiz">Raiz</option>
        </select>
      </div>
      <div class="resultado mt-5">
        <p>{{ estado.resultado }}</p>
      </div>
    </div>
  </body>
</template>

<style scoped>
* {
  color: #fff;
  box-sizing: border-box;
}

body {
  background-color: #07070f;
  margin: 0;
  font-family: Arial, sans-serif;
}

.container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  text-align: center;
}

.numeros {
  display: flex;
  gap: 15px;
  justify-content: center;
  margin-top: 20px;
}

.numeros input {
  width: 100px;
  padding: 10px;
  border: none; 
  border-radius: 5px; 
  font-size: 1rem;
  background: linear-gradient(#ffffff, #ffffff) padding-box, 
              linear-gradient(45deg, #ff0000, #ff9900, #ff00ff) border-box; 
  border: 3px solid transparent; 
  color: #07070f;
}

.operadores{
  margin-top: 3em;
}

.operador-seletor {
  width: 200px;
  padding: 10px;
  border: none;
  border-radius: 10px;
  font-size: 1rem;
  color: #ffffff;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.3);
  background: linear-gradient(#1f1f2e, #1f1f2e) padding-box, 
              linear-gradient(45deg, #ff0000, #ff9900, #ff00ff) border-box; 
  border: 3px solid transparent; 
  background-color: #1f1f2e;
}

.resultado{
  width: 150px;
  margin: 0 auto;
  background: linear-gradient(#07070f, #07070f) padding-box, 
              linear-gradient(45deg, #ff0000, #ff9900, #ff00ff) border-box; 
  border: 3px solid transparent; 
  border-radius: 5px;
}
.resultado p {
  margin-top: 1rem;
}
</style>
