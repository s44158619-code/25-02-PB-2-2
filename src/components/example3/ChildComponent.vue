<template>
  <div>
    <p>{{ message }}</p>
    <p>{{ id }}</p>
    <p>{{ password }}</p>

    <button @click="$emit('custom-event', 'Hello from child')">Send Event</button>
  </div>
</template>

<script lang="ts" setup>
import { defineProps, defineEmits } from 'vue';

// Options API의 props: [...]를 defineProps로 대체
const props = defineProps({
  message: String,
  id: Number,
  password: Number
});

// 컴포넌트가 발생시키는 이벤트를 명시적으로 선언
defineEmits(['custom-event']);
</script>