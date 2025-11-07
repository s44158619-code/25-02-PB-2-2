<template>
  <div>
    <ChildComponent1 />
  </div>
</template>

<script lang="ts" setup>
import { provide } from 'vue';
import ChildComponent1 from "@/components/example4/ChildComponent1.vue";

provide('sharedMessage', 'Hello from provide');
</script>