<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  title: String
});
</script>

<template>
  <section>
    <h2 v-if="props.title">{{ props.title }}</h2>
    <slot/>
  </section>
</template>

<style scoped>
section {
  max-width: 700px;
  margin: 0 auto 32px;
}
h2 {
  margin-bottom: 8px;
  font-weight: 700;
  line-height: 1.5;
  font-size: 24px;
}
</style>
