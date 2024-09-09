<script setup lang="ts">
import { ref } from 'vue'

const monTableau = ref([
  { todo: 'apprendre Vue Js', done: false },
  { todo: 'apprendre à faire des boucles', done: false },
  { todo: 'apprendre à griller des saucisses', done: true }
])
</script>
<template>
  <div>
    <span v-if="monTableau.length % 2 === 0">Mon tableau est pair</span>
    <span v-else>Mon tableau est impaire</span>
    <span v-for="element in monTableau" :key="element.todo">
      mon élément est {{ element.todo }}
      <input type="checkbox" :checked="element.done" />
      <br />
    </span>
  </div>
</template>
