<template>
  <Section title="Educación" >

        <article>

            <div>
              <h3>{{ data.institution }}</h3>
              <h4>{{ data.area }}</h4>
            </div>
            <time>
              {{ new Date(data.startDate).getFullYear() }} - 
              {{ data.endDate ? new Date(data.endDate).getFullYear() : 'Presente' }}
            </time>

        </article>

  </Section>
</template>

<script setup>
import Section from '../components/Section/Section.vue';

const props = defineProps({
  data: {
    type: Array, 
    default: () => ([]),
  },
});
</script>

<style scoped>
  article h3{
    font-weight: 600;
    color: #111;
  }

  article h4{
    color: #222;
    font-weight: 400;
  }

  article{
    display: flex;
    justify-content: space-between;
    align-content: flex-start;
    margin-bottom: 4px;
  }

  time{
    color: #555;
    font-size: 0%85rem ;
  }
</style>
