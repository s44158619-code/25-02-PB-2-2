<template>
  <E12RefComponent/>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import E01Instance from "@/components/example1/E-01-instance.vue";
import E02Reactive from "@/components/example1/E-02-reactive.vue";
import E03Binding from "@/components/example1/E-03-binding.vue";
import E04Directives from "@/components/example2/E-04-directives.vue";
import E05ParentComponent from "@/components/example3/ParentComponent.vue";
import E06ParentComponent from "@/components/example4/ParentComponent.vue";
import E07OptionsApi from "@/components/example5/E-07-Options-API.vue";
import E08CompositionApi from "@/components/example5/E-08-composition-api.vue";
import E10Ref from "@/components/example6/E-10-ref.vue";
import E12RefComponent from "@/components/example6/E-12-ref-component.vue";

export default defineComponent({
  name: 'App',
  components: {
    E12RefComponent
  }
});
</script>

<style>
</style>
