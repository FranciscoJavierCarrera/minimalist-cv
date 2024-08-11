<template>
  <Section title="Proyectos">
    <ul>
      <li v-for="work in data" :key="work.name">
        <article>
          <header>
            <div>
            <h3>
              <a :href="`${work.url}`" :title="`ver el proyecto ${work.name}`">
              {{ work.name }}
              </a>
              <p>{{ work.description }}</p>
            </h3>
            </div>
          </header>
          <footer>
            <span v-for="highlight in work.highlights" :key="highlight">{{ highlight }}</span>
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
    display: grid;
    grid-template-columns: repeat(auto-fit,minmax(200px,1fr));
    gap:1rem;
  }
  article{
    border-radius: 8px;
    border: 1px solid #f2f2f2;
    gap: 16px;
    display: flex;
    flex-direction: column;
    padding: 16px;
    height: 100%;
  }

  article header{
    flex: 1;
  }

  article h3{
    margin-bottom: 4px;
  }

  article a{
    color: #111;
  }

  article a:hover{
    text-decoration: underline;
  }

  footer{
    display: flex;
    flex-wrap: wrap;
    gap: 4px;
    font-size: 0.6rem;
  }

  footer span{
    border-radius: 6px;
    background: #eee;
    color:#333;
    font-size: 0.8rem;
    font-weight: 500;
    padding: 0.2rem 0.6rem;
  }

</style>