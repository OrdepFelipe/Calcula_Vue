<script setup>
import { reactive } from 'vue';

const estado = reactive({
  primeiroNumero: 0,
  segundoNumero: 0,
  selectedOperation: 'somar', // Operação padrão inicial
});

function calcularResultado() {
  const { primeiroNumero, segundoNumero, selectedOperation } = estado;

  switch (selectedOperation) {
    case 'somar':
      return primeiroNumero + segundoNumero;
    case 'subtrair':
      return primeiroNumero - segundoNumero;
    case 'dividir':
      return primeiroNumero / segundoNumero;
    case 'multiplicar':
      return primeiroNumero * segundoNumero;
    default:
      return null;
  }
}
</script>

<template>
  <div class="container__input">
    <input v-model.number="estado.primeiroNumero" type="number" placeholder="Insira o primeiro número">
    <input v-model.number="estado.segundoNumero" type="number" placeholder="Insira o segundo número">

    <select v-model="estado.selectedOperation">
      <option value="somar">Somar</option>
      <option value="subtrair">Subtrair</option>
      <option value="dividir">Dividir</option>
      <option value="multiplicar">Multiplicar</option>
    </select>

    <p v-if="resultado !== null" class="resultado">Resultado: {{ calcularResultado() }}</p>
  </div>
</template>

<style scoped>
.container__input {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-top: 20px;
}

.input {
  margin-bottom: 10px;
  text-align: center;
}

.resultado {
  margin-top: 10px;
  font-weight: bold;
}
</style>