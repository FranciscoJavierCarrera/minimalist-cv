<script setup>
import { ref, onMounted } from 'vue';

import About from './components/About.vue';
import Education from './components/Education.vue';
import Experience from './components/Experience.vue';
import Hero from './components/Hero.vue';
import Projects from './components/Projects.vue';
import Skills from './components/Skills.vue';

const cvData = ref({
  basics:{}
});

onMounted(async () => {
  try {
    const response = await fetch('/cv.json');
    if (response.ok) {
      cvData.value = await response.json();
      console.log(cvData.value.basics);
    } else {
      console.error('Error al cargar cv.json:', response.statusText);
    }
  } catch (error) {
    console.error('Error al convertir cv.json:', error);
  }
});
</script>

<template>
  <div id="app">
    <Hero :data="cvData.basics"/>
    <About :data="cvData.basics.summary"/>
    <Experience :data="cvData.work"/>
    <Education :data="cvData.education"/>
    <Projects :data="cvData.projects"/>
    <Skills :data="cvData.skills"/>
  </div>
</template>

<style >
html {
  font-family: Menlo,Monaco, Lucida Console, nomospace;
  background: #fff;
  letter-spacing: -0.025rem;
  }
  body,
  figure{
    margin: 0;
    padding: 0;
  }
  a {
    text-decoration: none;
  }
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }

  *,**::before, *::after{
    box-sizing: border-box;
  }

  @media (prefers-color-scheme : dark) {
    html{
      background: #000;
      color: #fff;
    }
  }
  h1,h2,h3,h4{
    margin : 0;
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }
  p{
    color: #666;
    font-size: .8rem;
    line-height: 1.5;
    margin: 0; 
  }
  main{
    padding: 4rem;
    margin: auto;
    width: 100%;
  }

  .print{
    display: none;
  }

  @media print{
    .print{
      display: block;
    }
    .no-print{
      display: none;
    }
  }
</style>
