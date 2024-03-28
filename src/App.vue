<script setup>

  import { reactive } from 'vue';

  const estado = reactive({
    numA: 0,
    numB: 0,
    resultado: 0,
    filtro: 'adicao'
  });

  function adicao(numA, numB){
    estado.resultado = numA + numB; 
    return estado.resultado;
  }

  function subtracao(numA, numB){
    estado.resultado = numA - numB;
    return estado.resultado;
  }

  function divisao(numA, numB){
    estado.resultado = numA / numB;
    return estado.resultado;
  }

  function multiplicacao(numA, numB){
    estado.resultado = numA * numB;
    return estado.resultado;
  }

  const calculadora = () => {
    
    switch(estado.filtro) {

      case 'subtracao':
        return subtracao(estado.numA, estado.numB);
      case 'divisao':
        return divisao(estado.numA, estado.numB);
      case 'multiplicacao':
        return multiplicacao(estado.numA, estado.numB);
      default:
        return adicao(estado.numA, estado.numB);

    }

  }

</script>

<template>
  <div class="container">
    <header class="p-5 mt-4 mb-4 bg-light rounded">
      <h1>Realizando calculos</h1>
      <p>Fazendo os calculos com você</p>
    </header>
    <form>
      <div class="row">
        <div class="col-md-5">
          <input @change='event => estado.numA = parseFloat(event.target.value)' type="number" placeholder="Digite o primeiro" class="form-control">
        </div>
        <div class="col-md-5">
          <input @keyup="event => estado.numB = parseFloat(event.target.value)" type="number" placeholder="Digite o segundo numero" class="form-control">
        </div>
        <div class="col-md-2">
          <select v-model="estado.filtro" @change="calculadora" class="form-control">
            <option value="adicao">Adiçao</option>
            <option value="subtracao">Subtração</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
          </select>
        </div>
      </div>
    </form>
    <div class="row">
      <div class="col">
        <span>
          {{ estado.resultado }}
        </span>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>
