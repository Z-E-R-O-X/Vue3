<template>
    <div>
        <h1 :style="{ fontSize: `${fontSize}px` }">Componente 2</h1>
        <div>
            <button @click="enlarge" style="margin-right: 10px;">Agrandar</button>
            <button @click="reduce">Reducir</button>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const fontSize = ref(16);

const enlarge = () => {
    fontSize.value += 2;
};

const reduce = () => {
    fontSize.value -= 2;
    if (fontSize.value < 12) {
        fontSize.value = 12;
    }
};
</script>
<style>
button {
  margin-bottom: 100px;
}
</style>