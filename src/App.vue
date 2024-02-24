<template>
  <div class="container">

    <input class="campo" @keyup="evento => estado.transferindo = evento.target.value" type="number" placeholder="Quantia para transferir">
    <input class="campo2" @keyup="evento => estado.transferindo2 = evento.target.value" type="number" placeholder="Quantia para transferir">
    
    <select v-model="test" @change="evento => estado.filtro = evento.target.value">
      <option class="list" value="10"> Multiplicação </option>
      <option class="list" value="20"> Divisão </option>
      <option class="list" value="30"> Subtração </option>
      <option class="list" value="40"> Adição </option>
    </select>
    <br>
    <Span v-if="10 == estado.filtro" >Resultado final da Multiplicação: {{ funcMult() }} </Span><br>
    <Span v-if="20 == estado.filtro">Resultado final da Divisão: {{ funcDiv() }} </Span><br>
    <Span v-if="30 == estado.filtro">Resultado final da Subtração: {{ funcSub() }} </Span><br>
    <Span v-if="40 == estado.filtro">Resultado final da Adição: {{ funcAdicao() }} </Span><br>
  </div>
</template>


<script setup>
import { reactive, ref } from 'vue';

  const estado = reactive({
    filtro: 'multiplicacao',
    transferindo: 0,
    transferindo2: 0,
  })

  function funcMult() {
    const {transferindo, transferindo2 } = estado
      return transferindo * transferindo2;
  }

  function funcDiv() {
    const {transferindo, transferindo2 } = estado
      return transferindo / transferindo2;
  }

  function funcSub() {
    const {transferindo, transferindo2 } = estado
      return transferindo - transferindo2;
  }

  function funcAdicao() {
    const {transferindo, transferindo2 } = estado
      return parseInt(transferindo) + parseInt(transferindo2);
  }
</script>

<style scoped>

.container{
  margin-top: 200px;
  margin-left: 200px;
  font-size: 20px;

}

template {
  background-color: yellowgreen;
  
}

.campo,
.campo2,
span {
  font-size: 20px;
}

span {
  font-size: 30px;
}
</style>