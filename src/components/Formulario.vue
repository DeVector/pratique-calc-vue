<script setup>

    const props = defineProps(['numA', 'numB', 'filtroCalc', 'filtroEstado'])
</script>

<template>
    <form>
      <div class="row">
        <div class="col-md-5">
          <input @change='props.numA' type="number" placeholder="Digite o primeiro" class="form-control">
        </div>
        <div class="col-md-5">
          <input @keyup="props.numB" type="number" placeholder="Digite o segundo numero" class="form-control">
        </div>
        <div class="col-md-2">
          <select v-model="props.filtroEstado" @keyup="props.filtroCalc" class="form-control">
            <option value="adicao">Adiçao</option>
            <option value="subtracao">Subtração</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
          </select>
        </div>
      </div>
    </form>
</template>