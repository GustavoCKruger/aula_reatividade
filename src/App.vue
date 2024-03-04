<script setup>
import { ref, reactive, computed } from 'vue';

const contadores = reactive({
  contador: ref(0),
  segContador: ref(0),
})

function incrementar() {
  contadores.contador++;
}

function decrementar() {
  if (contadores.contador > 0) {
    contadores.contador--;
  }
}

function incrementar2() {
  contadores.segContador++;
}

function decrementar2() {
  if (contadores.segContador > 0) {
    contadores.segContador--;
  }
}

const maior = computed(() => {
  return (contadores.contador + contadores.segContador) > 10;
});

const par = computed(() => {
  return (contadores.contador + contadores.segContador) % 2 == 0;
});


</script>

<template>
  <div>
    <div class="contador">
      <h2>Contador</h2>
      <p>Valor: {{ contadores.contador }}</p>
      <button @click="incrementar()">incrementar</button>
      <button @click="decrementar()">decrementar</button>
    </div>

    <div class="contador2">
      <h2>Contador 2</h2>
      <p>Valor: {{ contadores.segContador }}</p>
      <button @click="incrementar2()">incrementar</button>
      <button @click="decrementar2()">decrementar</button>
    </div>
    <div>
      <input type="text" class="result" disabled :placeholder="contadores.contador + contadores.segContador">
      <p v-if="!maior">Valor menor que 10!</p>
      <p v-else>Valor maior que 10!</p>
      <p v-if="!par">O número é ìmpar</p>
      <p v-else>O número é par</p>
    </div>
  </div>
</template>

<style scoped>
.contador {
  margin-right: 30px;
}
.result{
  color: black;
}
</style>
