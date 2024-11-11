<script setup>
import { reactive } from 'vue';

const estado = reactive({
    numero1: 0,
    numero2: 0,
    resultado: 0,
    operacao: 'somar'
});

const calcular = () => {
    const n1 = parseFloat(estado.numero1);
    const n2 = parseFloat(estado.numero2);

    switch (estado.operacao) {
        case 'somar':
            estado.resultado = n1 + n2;
            break;
        case 'subtrair':
            estado.resultado = n1 - n2;
            break;
        case 'multiplicar':
            estado.resultado = n1 * n2;
            break;
        case 'dividir':
            estado.resultado = n2 !== 0 ? n1 / n2 : 'Erro: Divisão por zero';
            break;
    }
};
</script>

<template>
  <header>
    <input @input="evento => { estado.numero1 = evento.target.value; calcular(); }" type="number" placeholder="Insira o primeiro número">
    <input @input="evento => { estado.numero2 = evento.target.value; calcular(); }" type="number" placeholder="Insira o segundo número">
    <select @change="evento => { estado.operacao = evento.target.value; calcular(); }">
      <option value="somar">somar</option>
      <option value="subtrair">subtrair</option>
      <option value="multiplicar">multiplicar</option>
      <option value="dividir">dividir</option>
    </select>
    <h1>Resultado: {{ estado.resultado }}</h1>
  </header>
</template>

<style scoped>
</style>
