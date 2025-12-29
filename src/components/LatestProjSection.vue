<template>
  <section class="text-white mt-20" id="projects">
    <div class="px-4 xl:pl-16">
      <div class="mb-4 md:flex md:justify-between xl:pr-16">
        <h2 class="text-4xl font-bold text-white">Mis Últimos Proyectos</h2>
        <!-- Filtro de categorías -->
        <div class="flex space-x-4 mb-4 mt-5 md:mt-0">
          <button 
            v-for="category in categories"
            :key="category.value"
            @click="selectedCategory = category.value"
            :class="[
              'px-4 py-2 rounded-full border transition-colors',
              selectedCategory === category.value ? 'bg-slate-700 text-white' : 'border-slate-200 hover:bg-slate-700 hover:text-white'
            ]"
          >
            {{ category.label }}
          </button>
        </div>
      </div>
      
      <!-- Grid de Proyectos -->
      <ul 
        class="px-4 sm:py-16 xl:pr-16 grid grid-cols-1 gap-6 pt-10 sm:grid-cols-2 md:gap-10 md:pt-12 lg:grid-cols-3"
        data-aos="fade-right"
      >
        <li 
          v-for="project in filteredProjects" 
          :key="project.id"
          class="max-w-md mx-auto"
        >
          <!-- Contenedor principal de la tarjeta -->
          <div class="bg-[#111a3e] text-white rounded-xl shadow-lg border border-[#1f1641] overflow-hidden">
            
            <!-- Imagen / Overlay -->
            <div class="relative group">
              <img 
                :src="project.image" 
                :alt="project.title" 
                class="w-full h-52 md:h-[24rem] object-contain" 
              />
              <!-- Overlay -->
              <div 
                class="overlay items-center justify-center absolute top-0 left-0 w-full h-full bg-[#181818] bg-opacity-0
                flex opacity-0 group-hover:opacity-100 transition-opacity duration-500"
              >
                <template v-if="project.webURL || project.gitURL">
                  <!-- Enlace al sitio web con ícono de “ojo” -->
                  <a 
                    v-if="project.webURL"
                    class="h-14 w-14 mr-2 border-2 relative rounded-full border-[#ADB7BE] hover:border-white group/link"
                    :href="project.webURL" 
                    target="_blank" 
                    rel="noopener noreferrer"
                  > 
                    <!-- Ícono de “ojo” -->
                    <svg 
                      xmlns="http://www.w3.org/2000/svg" 
                      fill="none"
                      viewBox="0 0 24 24" 
                      stroke-width="1.5" 
                      stroke="currentColor" 
                      aria-hidden="true"
                      data-slot="icon"
                      class="h-10 w-10 text-[#ADB7BE] absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 cursor-pointer group-hover/link:text-white"
                    >
                      <path 
                        stroke-linecap="round" 
                        stroke-linejoin="round"
                        d="M2.036 12.322a1.012 1.012 0 0 1 0-.639C3.423 7.51 7.36 4.5 12 4.5c4.638 0 8.573 3.007 9.963 7.178.07.207.07.431 0 .639C20.577 16.49 16.64 19.5 12 19.5c-4.638 0-8.573-3.007-9.963-7.178Z"
                      ></path>
                      <path 
                        stroke-linecap="round" 
                        stroke-linejoin="round"
                        d="M15 12a3 3 0 1 1-6 0 3 3 0 0 1 6 0Z"
                      ></path>
                    </svg>
                  </a>
      
                  <!-- Enlace al repositorio Git con ícono de “código” -->
                  <a
                    v-if="project.gitURL"
                    class="h-14 w-14 border-2 relative rounded-full border-[#ADB7BE] hover:border-white group/link"
                    :href="project.gitURL" 
                    target="_blank" 
                    rel="noopener noreferrer"
                  > 
                    <!-- Ícono de “código” -->
                    <svg 
                      xmlns="http://www.w3.org/2000/svg" 
                      fill="none"
                      viewBox="0 0 24 24" 
                      stroke-width="1.5" 
                      stroke="currentColor" 
                      aria-hidden="true"
                      data-slot="icon"
                      class="h-10 w-10 text-[#ADB7BE] absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 cursor-pointer group-hover/link:text-white"
                    >
                      <path 
                        stroke-linecap="round" 
                        stroke-linejoin="round"
                        d="M17.25 6.75 22.5 12l-5.25 5.25m-10.5 0L1.5 12l5.25-5.25m7.5-3-4.5 16.5"
                      ></path>
                    </svg>
                  </a>
                </template>
                <template v-else>
                  <span class="text-lg font-semibold">Proyecto Privado</span>
                </template>
              </div>
            </div>
    
            <!-- Info del Proyecto -->
            <div class="py-6 px-4">
              <h3 class="text-lg font-semibold uppercase lg:text-xl">{{ project.title }}</h3>
              <p class="text-[#ADB7BE]">{{ project.description }}</p>
              <div class="flex flex-wrap p-2.5">
                <div 
                  v-for="technology in project.technologies" 
                  :key="technology" 
                  class="text-center ml-1 mt-1 rounded-3xl bg-[#111827]"
                  style="box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1); border: 1px solid #111827; backdrop-filter: blur(9px); -webkit-backdrop-filter: blur(9px);"
                >
                  <p class="px-1 py-2">{{ technology }}</p>
                </div>
              </div>
            </div>
          </div>
        </li>
      </ul>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue';
import portfolioImage from '../assets/portafolio.webp'; // Importa tu imagen
import notasrustImage from '../assets/notasrustweb.webp';

// Definimos las categorías en español
const categories = [
  { value: 'all', label: 'Todos' },
  { value: 'web development', label: 'Desarrollo Web' },
  { value: 'Mobile App', label: 'App Móvil' }
];

const Projects = ref([
  {
    id: 4,
    category: 'web development',
    image: notasrustImage, 
    title: 'Notas Serverless (Rust + Vue)',
    description: 'Una aplicación de notas moderna y rápida construida con Vue 3, Tailwind CSS, y respaldada por una arquitectura serverless en Rust sobre AWS Lambda.',
    technologies: ['Vue 3', 'Tailwind CSS', 'Rust', 'AWS Lambda', 'DynamoDB'],
    gitURL: 'https://github.com/HernanEspinozaDev/notasrust-frontend', 
    webURL: 'https://notasrust.testingpage.store/'
  },
  {
    id: 1,
    category: 'web development',
    image: 'https://candelmed.com/image/CandelAzul.png', 
    title: 'Candel',
    description: 'Desarrollo privado para una startup durante 4 meses (agosto a noviembre de 2024). Utilicé React, Next y AWS Amplify. Trabajo colaborativo en GitHub con los integrantes del equipo. Participé en la implementación del dashboard, interacciones de la página, menús y submenús.',
    technologies: ['React', 'Next.js', 'AWS Amplify'],
    gitURL: '', // Proyecto privado
    webURL: 'https://www.candelmed.com/'
  },
  {
    id: 2,
    category: 'Mobile App',
    image: 'https://play-lh.googleusercontent.com/SrM1FfUasnMCDPTwkYbDDxUJlT46Mln5-teGhZ7IyNo9Ujf16g7sI4gAe78r3mxRKRA=w240-h480-rw', 
    title: 'CandelApp',
    description: 'Desarrollo privado para una startup durante 4 meses (agosto a noviembre de 2024). Utilicé React Native CLI. Trabajo colaborativo en GitHub con los integrantes del equipo. Implementación de vistas y tutoriales para juegos, integración de calendarios y funcionalidades, manejo de la base de datos y refactorización de funciones.',
    technologies: ['React Native CLI', 'AWS Amplify'],
    gitURL: '', // Proyecto privado
    webURL: 'https://play.google.com/store/apps/details?id=com.candelapp&hl=es_CL&gl=US'
  },
  {
    id: 3,
    category: 'web development',
    image: portfolioImage, // Usa la imagen importada
    title: 'Portafolio',
    description: 'Portafolio hecho en Vue con Vite y Tailwind CSS. Página: hernanespinozadev.website.',
    technologies: ['Vue.js', 'Vite', 'Tailwind CSS'],
    gitURL: 'https://github.com/HernanEspinozaDev/portfolio',
    webURL: 'https://portfolio.hotusoft.com/'
  },
]);

const selectedCategory = ref('all');

// Filtra los proyectos según la categoría seleccionada
const filteredProjects = computed(() => {
  if (selectedCategory.value === 'all') {
    return Projects.value;
  }
  return Projects.value.filter(
    project => project.category.toLowerCase() === selectedCategory.value.toLowerCase()
  );
});
</script>

<style scoped>
/* Estilos adicionales si lo deseas */

/* Opcional: Mejora la visibilidad del overlay al hacer hover */
.overlay {
  background-color: rgba(24, 24, 24, 0.8);
}
</style>
