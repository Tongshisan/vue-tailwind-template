<script setup lang="ts">
import { ref } from "vue";
import Typewriter from "./components/typewriter/index.vue";

const count = ref(0);

const callback = () => {
  console.log("callback");
};
</script>

<template>
  <button @click="count++">Count is: {{ count }}</button>
  <Typewriter content="Hello, World!" :callback="callback" />
</template>
