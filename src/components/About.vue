<template>
    <Section title="Acerca de mi">
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