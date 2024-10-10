<template>
    <Section title="About Me">
        <p>
            {{ data }}
        </p>
    </Section>
 
</template>

<script setup>
import Section from '../components/Section/Section.vue';

const props = defineProps({
  data: {
    type: Object,
    default: () => ({})
  }
});
</script>

<style>
   
</style>