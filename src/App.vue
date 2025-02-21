<script setup lang="ts">
import { ref } from "vue";
import Typewriter from "./components/typewriter/index.vue";

const count = ref(0);
</script>

<template>
  <button @click="count++">Count is: {{ count }}</button>
  <Typewriter content="Hello, World!" />
</template>
