<template>
 
 
 <Section title="Education">  <ul>
      <li v-for="work in data" :key="work.institution">
        <article>
          <header>
            <div>
              <h3>{{ work.institution }}</h3>
              <h4>{{ work.area }}</h4>
            </div>
            <time>
              {{ new Date(work.startDate).getFullYear() }} - 
              {{ work.endDate ? new Date(work.endDate).getFullYear() : 'Presente' }}
            </time>
          </header>

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
    font-weight: 500;
    color: #111;
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
  footer{
        display: flex;
        gap: 4px;
        margin-top:8px;
    }

    footer a{
        color: #777;
        display: inline-flex;
        align-content: center;
        justify-content: center;
        border: 1px solid #eee;
        padding: 4px;
        height: 32px;
        width: 32px;
        border-radius: 6px;
        transition: all .3s ease;
    }
    footer a:hover{
        background: #eee;
    }
</style>
