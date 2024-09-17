<script setup lang="ts">
import TodolistComp from '@/components/TodolistComp.vue';
import { ref, onMounted } from 'vue';

const monTableau = ref<any[]>([]);

onMounted(async () => {
  const todosRequest = await fetch('http://localhost:3000/todos');
  const todos = await todosRequest.json();
  monTableau.value = [...todos];
});

const onTodoInput = (newTodoValue: any, index: number) => {
  monTableau.value[index] = newTodoValue;
  console.log('monTableau est mis à jour');
};
const newTodo = ref();

const addTodo = () => {
  if (newTodo.value.trim() !== '') {
    monTableau.value.push({ todo: newTodo.value.trim(), done: false });
    newTodo.value = '';
  }
};

const onDelete = (index: number) => {
  monTableau.value.splice(index, 1);
};
</script>

<template>
  <main>
    <TodolistComp
      v-for="(element, index) in monTableau"
      :todo="element"
      v-bind:key="index"
      @onInput="onTodoInput($event, index)"
      @onDelete="() => onDelete(index)"
    />
    <span>
      <input v-model="newTodo" placeholder="Ajouter une nouvelle tâche" />
      <button @click="addTodo">Ajouter</button>
    </span>
  </main>
</template>
