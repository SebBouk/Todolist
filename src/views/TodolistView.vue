<script setup lang="ts">
import TodolistComp from '@/components/TodolistComp.vue'
import { ref } from 'vue'

const monTableau = ref([
  { todo: 'apprendre Vue Js', done: false },
  { todo: 'apprendre à faire des boucles', done: false },
  { todo: 'apprendre à griller des saucisses', done: true }
])
const onTodoInput = (newTodoValue: any, index: number) => {
  monTableau.value[index] = newTodoValue
  console.log('monTableau est mis à jour')
}
</script>

<template>
  <main>
    <TodolistComp
      v-for="(element, index) in monTableau"
      :todo="element"
      v-bind:key="index"
      @onInput="onTodoInput($event, index)"
    />
  </main>
</template>
