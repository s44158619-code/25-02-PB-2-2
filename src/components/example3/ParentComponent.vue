<template>
  <div>
    <ChildComponent
        :message="parentMessage"
        :id="1"
        :password="1234"
        @custom-event="handleEvent"
    />
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';
import ChildComponent from './ChildComponent.vue';

const parentMessage = ref('Hello from parent');

const handleEvent = (payload: any) => { // (TS) payload 타입을 any 또는 구체적인 타입으로 지정
  console.log(payload);
};
</script>