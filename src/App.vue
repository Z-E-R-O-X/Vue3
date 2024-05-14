<script setup>
import MiComponente from './components/MiComponente.vue';
import AgrandarTexto from './components/AgrandarTexto.vue';
import { ref, computed } from "vue";

const name = "Vue 3";

const counter = ref(0);
const arrayCounter = ref([]);

const increment = () => {
  counter.value++;
};

const decrement = () => {
  counter.value--;
};

const reset = () => {
  counter.value = 0;
};

const add = () => {
  arrayCounter.value.push(counter.value);
};

const remove = () => {
  arrayCounter.value.pop(counter.value);
};

const blockNumber = computed(() => {
  const number = arrayCounter.value.find((num) => num === counter.value);
  return number || number === 0;
});

const classCounter = computed(() => {
  if (counter.value === 0) {
    return "zero";
  }
  return counter.value > 0 ? "positive" : "negative";
});

const listacolor = {};

const color_azar = () => {
  const colores = ['#007bff', '#6c757d', '#28a745', '#dc3545', '#ffc107',
    '#17a2b8', '#6610f2', '#fd7e14', '#20c997', '#6f42c1',
    '#ff5c5c', '#64dd17', '#ff5722', '#00bcd4', '#4caf50',
    '#ffeb3b', '#9c27b0', '#e91e63', '#9e9e9e', '#795548',
    '#607d8b', '#f44336', '#2196f3', '#ff9800', '#03a9f4',
    '#8bc34a', '#ffc107', '#9c27b0', '#ff5722', '#00bcd4',
    '#4caf50', '#ffeb3b', '#9c27b0', '#e91e63', '#9e9e9e',
    '#795548', '#607d8b', '#f44336', '#2196f3', '#ff9800',
    '#03a9f4', '#8bc34a', '#ffc107', '#9c27b0', '#ff5722',
    '#00bcd4', '#4caf50', '#ffeb3b', '#9c27b0', '#e91e63',
    '#9e9e9e', '#795548', '#607d8b', '#f44336', '#2196f3',
    '#ff9800', '#03a9f4', '#8bc34a', '#ffc107', '#9c27b0',
    '#ff5722', '#00bcd4', '#4caf50', '#ffeb3b', '#9c27b0',
    '#e91e63', '#9e9e9e', '#795548', '#607d8b', '#f44336',
    '#2196f3', '#ff9800', '#03a9f4', '#8bc34a', '#ffc107',
    '#9c27b0', '#ff5722', '#00bcd4', '#4caf50', '#ffeb3b',
    '#9c27b0', '#e91e63', '#9e9e9e', '#795548', '#607d8b',
    '#f44336', '#2196f3', '#ff9800', '#03a9f4', '#8bc34a',
    '#ffc107', '#9c27b0', '#ff5722', '#00bcd4', '#4caf50',
    '#ffeb3b', '#9c27b0', '#e91e63', '#9e9e9e', '#795548',
    '#607d8b', '#f44336', '#2196f3', '#ff9800', '#03a9f4',
    '#8bc34a', '#ffc107', '#9c27b0', '#ff5722', '#00bcd4',
    '#4caf50', '#ffeb3b', '#9c27b0', '#e91e63', '#9e9e9e',
    '#795548', '#607d8b', '#f44336', '#2196f3', '#ff9800',
    '#03a9f4', '#8bc34a', '#ffc107', '#9c27b0', '#ff5722',
    '#00bcd4', '#4caf50', '#ffeb3b', '#9c27b0', '#e91e63',
    '#9e9e9e', '#795548', '#607d8b', '#f44336', '#2196f3',];
  return colores[Math.floor(Math.random() * colores.length)];
};

const obtener_color = (item) => {
  if (listacolor
[item]) {
    return listacolor
  [item];
  } else {
    const color = color_azar
  ();
    listacolor
  [item] = color;
    return color;
  }
};
</script>

<template>
  <div class="container text-center" style="width: 100%; margin: 20px; border: 3px solid blue; padding: 20px;">
    <h1 class="text-white">Hola {{ name }}!</h1>
    <h2 :class="classCounter">
      {{ counter }}
    </h2>

    <div class="btn-group">
      <button @click="reset" class="btn btn-secondary">Reset</button>
      <button @click="increment" class="btn btn-success">Incremet</button>
      <button @click="decrement" class="btn btn-warning">Decrement</button>
      <button @click="add" :disabled="blockNumber" class="btn btn-primary">Add</button>
      <button @click="remove" class="btn btn-danger">Remove</button>
    </div>
  </div>
  <div style="width: 100%; margin: 20px; border: 3px solid blue; padding: 20px;">
    <h2 style="margin-bottom: 20px; text-align: center; color: white;">Mis Favoritos</h2>
    <ul class="list-group list-group-horizontal listanumeros" style="margin: 20px;">
      <li class="list-group-item" v-for="(item, index) in arrayCounter" :key="index"
        :style="{ 'background-color': obtener_color(item) }">
        {{ item }}
      </li>
    </ul>
  </div>
  <div>
    <h1>Componente 1</h1>
    <MiComponente />
  </div>
  <div>
    <AgrandarTexto />
  </div>
</template>

<style>
body{
  background-color: rgb(34, 59, 59);
}
.listanumeros{
  display: flex;
  flex-wrap: wrap;
}

.negative {
  color: red;
}

.positive {
  color: green;
}

.zero {
  color: black;
}
</style>
