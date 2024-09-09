<script setup lang="ts">
import { ref } from 'vue';
const props = defineProps<{
  todo: { done: boolean; todo: string };
}>();
const emit = defineEmits(['onInput']);
const onInput = (value: boolean) => {
  console.log('TodoComponent a détecté un changement', value);
  emit('onInput', { ...props.todo, done: value });
};
const editMode = ref(false);
</script>

<template>
  <div v-if="!editMode">
    <span @click="editMode = !editMode">
      <!-- <span v-for="element in monTableau" :key="element.todo"> -->
      {{ props.todo.todo }}
    </span>
    <input
      type="checkbox"
      :checked="props.todo.done"
      @click="(event: any) => onInput(event.target?.checked)"
    />
    <br />
  </div>
  <span v-else>
    <input type="text" :value="props.todo.todo" />
    <button type="button" @click="editMode = !editMode">X</button>
  </span>
</template>
