<script setup lang="ts">
import { ref } from 'vue'

const monTableau = ref([1, 2, 3])
// const monTableau = [1, 2, 3,];

const ajouterElement = () => {
  monTableau.value.push(monTableau.value.length + 1)
  console.log(monTableau)
}
</script>

<template>
  <h1>Hello word !!!</h1>
  <span v-if="monTableau.lengh % 2 === 0">Mon tableau est pair</span>
  <span v-else>Mon tableau est impaire</span>
  <span v-for="element in monTableau" :key="element"> mon élément est {{ element }} </span>
  <button @click="ajouterElement">Ajouter une valeur</button>
  <!-- {{ monTableau }} -->
</template>

<style scoped></style>
