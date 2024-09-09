<script setup lang="ts">
// import { ref } from 'vue'
import HeaderComp from './components/HeaderComp.vue'

// const monTableau = ref([
//   { todo: 'apprendre Vue Js', done: false },
//   { todo: 'apprendre à faire des boucles', done: false },
//   { todo: 'apprendre à griller des saucisses', done: true }
// ])

// const monTableau = [1, 2, 3,];

// const ajouterElement = () => {
//   monTableau.value.push(monTableau.value.length + 1)
//   console.log(monTableau)
// }
</script>

<template>
  <HeaderComp />
  <h1>Hello word !!!</h1>
  <!-- <span v-if="monTableau.length % 2 === 0">Mon tableau est pair</span>
  <span v-else>Mon tableau est impaire</span>
  <span v-for="element in monTableau" :key="element.todo">
    mon élément est {{ element.todo }}
    <input type="checkbox" :checked="element.done" />
    <br />
  </span> -->
  <main>
    <RouterView />
  </main>

  <!-- <button @click="ajouterElement">Ajouter une valeur</button> -->
  <!-- {{ monTableau }} -->
</template>

<style scoped></style>
