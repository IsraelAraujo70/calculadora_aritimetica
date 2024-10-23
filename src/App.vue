<script setup>
import { reactive } from 'vue';
import Numeros from './components/Numeros.vue';
import SeletorDeOperacao from './components/SeletorDeOperacao.vue';
import Resultado from './components/Resultado.vue';

const estado = reactive({
  primeiro: 0,
  segundo: 0,
  resultado: 0,
  operadores: ['somar','subtracao','multiplicar','dividir','exponenciacao','raiz'],
  atual: ''
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
      estado.atual = estado.operadores[0]
      break;
    case 'subtracao':
      subtracao();
      estado.atual = estado.operadores[1]
      break;
    case 'multiplicar':
      multiplicar();
      estado.atual = estado.operadores[2]
      break;
    case 'dividir':
      dividir();
      estado.atual = estado.operadores[3]
      break;
    case 'exponenciacao':
      exponenciacao();
      estado.atual = estado.operadores[4]
      break;
    case 'raiz':
      raiz();
      estado.atual = estado.operadores[5]
      break;
  }
}
</script>

<template>
  <body>  
    <div class="container">
      <h1 class="mt-5 mb-5">Calculadora Aritimética</h1>
      <Numeros :primeiro-numero="evento => estado.primeiro = evento.target.value" :segundo-numero="evento => estado.segundo = evento.target.value" :operadores="realizarOperacao(estado.atual)"/>
      <SeletorDeOperacao :realizar-operacao="evento => realizarOperacao(evento.target.value)"/>
      <Resultado :resultado="estado.resultado"/>
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
</style>
