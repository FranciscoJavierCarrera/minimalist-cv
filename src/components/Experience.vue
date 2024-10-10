<template>
  <Section title="Experience">
    <ul>
      <li v-for="work in data" :key="work.name">
        <article>
          <header>
            <div>
              <h3>{{ work.name }}</h3>
              <h4>{{ work.position }}</h4>
            </div>
            <time>
              {{ new Date(work.startDate).toLocaleString('es-Mx', { month: 'short' }) }} {{ new Date(work.startDate).getFullYear() }} - 
              {{ work.endDate ? new Date(work.endDate).toLocaleString('es-MX', { month: 'short' }) : '' }} {{ work.endDate ? new Date(work.endDate).getFullYear() : 'Presente' }}
            </time>
          </header>
          <footer>
            <p>{{ work.summary }}</p>
          </footer>
        </article>
      </li>
    </ul>
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
  ul {
    display: flex;
    flex-direction: column;
    gap:32px;
  }

  article h3{
    color: #111;
    font-weight: 600;
  }

  article h4{
    color: #222;
    font-weight: 400;
  }

  header{
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
