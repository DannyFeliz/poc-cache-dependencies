<template>
  <div>Hello {{ name }}</div>
  {{ fullName }}
  <div>
    {{ log }}
  </div>
</template>

<script setup lang="ts">
import type { Ref } from "vue";
import { ref, computed, watch } from "vue";
import upperCase from "lodash/upperCase";

const name = ref("John");
const fullName = computed(() => {
  return name.value + " Doe";
})

watch(name, () => {
  log.value = "Name changed to: " + name.value;
})

const log: Ref<string> = ref("");

setTimeout(() => {
  name.value = upperCase("Maria");
}, 2000);


setTimeout(() => {
  name.value = "Pedro";
}, 3000);

</script>