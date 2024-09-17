<script setup lang="ts">
import { ref } from 'vue';

const props = defineProps<{
  todo: { done: boolean; todo: string };
}>();

const emit = defineEmits(['onInput', 'onDelete']);

const onInput = (value: boolean) => {
  console.log('TodoComponent a détecté un changement', value);
  emit('onInput', { ...props.todo, done: value });
};
const editMode = ref(false);

const newValue = ref(props.todo.todo);

const saveChanges = () => {
  emit('onInput', { ...props.todo, todo: newValue.value });
  editMode.value = false;
};

const cancelEdit = () => {
  newValue.value = props.todo.todo;
  editMode.value = false;
};
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
    /><button type="button" @click="$emit('onDelete')">Supprimer</button>
    <br />
  </div>
  <span v-if="editMode">
    <input type="text" v-model="newValue" />
    <button type="button" @click="saveChanges">✔</button>
    <button type="button" @click="cancelEdit">X</button>
    <br />
  </span>
  <!-- <button
      type="button"
      @click="
        props.todo.todo = newValue;
        editMode = !editMode;
      "
    >
      ✔
    </button>
  </span>
  <span v-if="editMode">
    <button
      type="button"
      @click="
        editMode = !editMode;
        newValue = props.todo.todo;
      "
    >
      X
    </button>
  </span> -->
</template>
