<template>
  <div>Hello, {{ message }}</div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';

const name = 'Kyungsu Lee';
const message = ref(name);
</script>

<style scoped>
div {
  color: blue;
  font-size: 20px;
  font-weight: bold;
}
</style>