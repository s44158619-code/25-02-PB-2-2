<template>
  <div>
    <input ref="inputField" type="text" placeholder="Click the button to focus" />
    <button @click="focusInput">Focus Input</button>
  </div>
</template>

<script lang="ts" setup>
import {ref, onMounted, onBeforeMount, onBeforeUpdate, onUpdated, onBeforeUnmount, onUnmounted} from 'vue';

const inputField = ref<HTMLInputElement | null>(null);

const focusInput = () => {
  if (inputField.value) {
    inputField.value.focus();
  }
};

onMounted(() => {
  console.log(inputField.value);
  if(inputField.value) {
    inputField.value.focus();
  }
});

onBeforeMount(() => console.log(inputField.value));
onMounted(() => console.log(inputField.value));
onBeforeUpdate(() => console.log(inputField.value));
onUpdated(() => console.log(inputField.value));
onBeforeUnmount(() => console.log(inputField.value));
onUnmounted(() => console.log(inputField.value));
</script>