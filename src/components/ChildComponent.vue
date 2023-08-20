<template>
  <div>
    <h1>Child Component</h1>
    <p>{{ props.message }}</p>
    <button @click="handleClick">Send Message</button>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  message: {
    type: String,
    required: true,
  },
});

const emitMessage = defineEmits(['messageEmitted']);

function handleClick() {
  emitMessage('messageEmitted', 'Hello from the child component!');
}
</script>
