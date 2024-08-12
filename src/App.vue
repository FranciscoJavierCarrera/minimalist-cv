<script setup>
import { ref, onMounted } from 'vue';

import About from './components/About.vue';
import Education from './components/Education.vue';
import Experience from './components/Experience.vue';
import Hero from './components/Hero.vue';
import Projects from './components/Projects.vue';
import Skills from './components/Skills.vue';
import "ninja-keys";

const cvData = ref({
  basics:{}
});

const hotkeys = ref([
  {
    id: "print",
    title: "Imprimir",
    hotkey: "ctrl+p",
    mdIcon: "",
    secction:"Acciones",
    handler: () => {
      window.print();
    },
  },
  
]);

onMounted(async () => {
  try {
    const response = await fetch('/cv.json');
    if (response.ok) {
      cvData.value = await response.json();
    } 
    if (Array.isArray(cvData.value.basics.profiles)) {
        cvData.value.basics.profiles.forEach(profile => {
          hotkeys.value.push({
            id: profile.network.toLowerCase(),
            title: profile.network,
            hotkey: `ctrl+${profile.network.charAt(0)}`, // Hotkey basado en la primera letra del network
            mdIcon: "", 
            secction: "Social",
            handler: () => {
              window.open(profile.url, '_blank');
            }
          });
        });
      } else {
        console.error("cvData.value.basics.profiles no es un array o está indefinido.");
      }

      console.log(hotkeys.value);
  } catch (error) {
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
    <ninja-keys class="no-print"
    @selected="selected"
    @change="change"
    :placeholder="placeholder"
    :data="hotkeys"
  ></ninja-keys>
  </div>
  <footer class="no-print footer" >
    Pulsa <kbd>crtl</kbd> + <kbd>k</kbd> para abrir la paleta de comandos
  </footer>
</template>

<style>

html {
  font-family: Courier,Lucida Console,'Courier New', monospace ;
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
    font-family: 'Courier New',Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    font-weight: bold;
  }
  p{
    color: #666;
    font-size: .8rem;
    line-height: 1.5;
    margin: 0; 
    font-family: Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
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
  #app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;

}
  main {
  flex: 1;
  padding: 4rem 1rem; 
  margin: auto;
  width: 100%;
  max-width: 800px;

}
</style>
<style scoped>

.footer {
  background: #fdfdfd;
  border-top: 1px solid #eee;
  text-align: center;
  padding-block: 14px;
  opacity: 1;
  transition: opacity 0.3s ease-in-out;
  position: sticky;
  bottom: 0;

}

.footer-show {
  opacity: 1;

}

/* Muestra el footer cuando se desplaza la página */
html:has(body:has(.scroll)) .footer {
  opacity: 1;

}

kbd {
  background: #eee;
  border-radius: 4px;
  padding: 2px 4px;
  font-size: 14px;
}
</style>