<template>
  <Section title="Habilidades">
    <div class="container">
      <ul v-for="skill in data" :key="skill.name" >

          <span>{{ skill.name }}</span>

            <li v-for="word in skill.keywords" :key="word">
              <p>{{ word }}</p>
            </li>


      </ul>
    </div>
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

.container {
  display: grid;
  grid-template-columns:1fr;
  gap: 1rem;
}


li{
  display: inline-flex;
  gap: 10px;
  flex-wrap: wrap;
}
p{
  border-radius: 6px;
  background: #eee;
  color: black;
  font-size: 0.8rem;
  font-weight: 500;
  padding: 0.2rem 0.6rem;
  margin-inline:  0.4rem;
  margin-bottom: 0.4rem;
}
span{
  border-radius: 6px;
  background: #777;
  color: #eee;
  font-size: 0.8rem;
  font-weight: 500;
  padding: 0.2rem 0.6rem;
}

</style>
