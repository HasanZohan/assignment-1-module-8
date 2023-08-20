<template>
  <div>
    <h1>Parent Component</h1>
    <p>{{ emittedMessage }}</p>
    <ChildComponent :message="props.message" @messageEmitted="handleMessageEmitted" />
  </div>
</template>

<script setup>
import ChildComponent from './ChildComponent.vue';
import { defineProps, ref, watch } from 'vue';

const props = defineProps({
  message: {
    type: String,
    required: true,
  },
});

const emittedMessage = ref('');

function handleMessageEmitted(newMessage) {
  emittedMessage.value = newMessage;
}

watch(
  () => props.message,
  (newValue) => {
    emittedMessage.value = newValue;
  }
);
</script>
