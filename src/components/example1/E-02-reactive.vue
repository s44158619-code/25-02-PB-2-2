<template>
  <div>{{ fullName }}</div>
</template>

<script lang="ts" setup>
import { ref, computed, onMounted } from 'vue';

// data
const firstName = ref("Kyungsu");
const lastName = ref("Lee");

// computed
const fullName = computed(() => {
  return firstName.value + " " + lastName.value;
});

// mounted
onMounted(() => {
  console.log('mounted');

  let a = 10;

  setTimeout(() => {
    console.log('setTimeout');
    a = 20;
    console.log(a);
  }, 500);

  setTimeout(() => {
    lastName.value = "123";
  }, 1000);

  setTimeout(() => {
    firstName.value = "KSL";
  }, 2000);
});
</script>