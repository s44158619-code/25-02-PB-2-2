<template>
  <div>
    <p>{{ sharedMessage }}</p>
  </div>
</template>

<script lang="ts" setup>
import { inject } from 'vue';

const sharedMessage = inject('sharedMessage');
</script>

<style scoped>
p {
  font-size: 1.5rem;
}
</style>