<template>
    <Section>
        <div class="container">
            <div class="info">
                <h1>{{ data.name }}</h1>
                <h2>{{ data.label }}</h2>
                <span>
                    {{ data.location?.city || 'Ciudad no disponible' }}, {{ data.location?.region || 'Región no disponible' }}
                </span>
                <footer>
                    <div class="no-print">
                        <a v-if="data.email" :href="`mailto:${data.email}`" :title="`Enviar un correo a ${data.name} al correo ${data.email}`" target="_blank">
                        <img src="@/assets/Icons/mail.svg" />
                        </a>
                        <a v-if="data.phone" :href="`tel:${data.phone}`" :title="`Llamar por teléfono a ${data.name} al número ${data.email}`" target="_blank">
                            <img src="@/assets/Icons/phone.svg"/>
                        </a>
                        <a v-for="red in data.profiles" :key="red.network" :href="`${red.url}`" :title="`Visitar  el perfil de ${data.name} en ${red.network}`" target="_blank"> 
                            <img v-if="red.network === 'GitHub'" src="@/assets/Icons/GitHub.svg" />
                            <img v-if="red.network === 'LinkedIn'" src="@/assets/Icons/LinkedIn.svg" />
                        </a>
                    </div>

                    <div class="print">
                        <span> {{ data.email }} &bull;  {{ data.phone }}  </span> 
                        <span v-for="red in data.profiles" :key="red.network">&bull; {{ red.url }} </span>

                    </div>

                </footer>
            </div>
            <figure >
                <img class="img_profile" :src="data.image" :alt="data.name" />
            </figure>
        </div>
    </Section>
</template>

<script setup>
import { defineProps } from 'vue';
import Section from '../components/Section/Section.vue';

// Definimos las props que recibe el componente
const props = defineProps({
  data: {
    type: Object,
    default: () => ({})
  }
});
</script>

<style scoped>
    .container{
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        gap: 1rem;
    }

    .info{
        display: flex;
        flex-direction: column;
        gap: 0.5rem;
        padding-right: 32px;
    }
    h1{
        font-size: 1.8rem;
        
    }
    h2{
        color: #444;
        font-weight: 500;
        font-size: 1.1rem;

    }
    .img_profile {
        aspect-ratio: 1/1;
        object-fit: cover;
        width: 128px;
        border-radius: 16px;
    }

    span{
        color:#666;
        display: flex;
        align-items: center;
        gap: 0.25rem;
        font-size: 0.85rem;
        letter-spacing: -0.05rem;
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
