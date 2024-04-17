<script setup>
  import { reactive, watchEffect } from "vue";

  const estado = reactive({
    numero1: 0,
    numero2: 0,
    operacao: 'soma',
    resultado: 0
  });

  
  const calcularResultado = () => {
    switch (estado.operacao) {
      case 'soma':
        estado.resultado = estado.numero1 + estado.numero2;
        break;
      case 'subtracao':
        estado.resultado = estado.numero1 - estado.numero2;
        break;
      case 'multiplicacao':
        estado.resultado = estado.numero1 * estado.numero2;
        break;
      case 'divisao':
        estado.resultado = estado.numero1 / estado.numero2;
        break;
      default:
        estado.resultado = 0;
    }
  };
  watchEffect(calcularResultado);
  </script>

<template>
    <div class="container">
    <input type="number" v-model="estado.numero1">
    <select v-model="estado.operacao">
      <option value="soma">+</option>
      <option value="subtracao">-</option>
      <option value="multiplicacao">*</option>
      <option value="divisao">/</option>
    </select>
    <input type="number" v-model="estado.numero2">
    <p>Resultado: {{ estado.resultado }}</p>
  </div>
</template>

<style scoped>

</style>
