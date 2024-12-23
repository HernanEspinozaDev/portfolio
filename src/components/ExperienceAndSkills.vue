<template>
    <section class="text-white mt-18" id="skills">
        <!-- Elemento Absoluto de Fondo -->
        <div class="absolute right-0 top-[110rem] h-full w-full justify-end flex pointer-events-none z-0">
            <span class="flex opacity-20">
                <span class="w-16 h-32 rounded-l-full flex bg-primary blur-2xl"></span>
                <span class="w-16 h-32 rounded-r-full flex bg-[#f88fc2] blur-2xl mt-14"></span>
            </span>
        </div>
        
        <!-- Contenedor Principal con z-index para asegurar que esté por encima del fondo -->
        <div class="md:grid md:grid-cols-2 gap-8 items-center py-8 px-4 xl:gap-16 xl:px-16 relative z-10">
            <!-- Sección de Habilidades -->
            <div>
                <h2 class="text-4xl font-bold text-white text-left mb-4">
                    Mis 
                    <span class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary">Habilidades</span>
                </h2>
                <div class="grid grid-cols-2 sm:grid-cols-3 gap-6 mt-8">
                    <div 
                        v-for="skill in Skills" 
                        :key="skill.id" 
                        class="group flex flex-col items-center bg-[#111a3e] shadow-lg border border-[#1f1641] rounded-xl p-4 transition transform hover:scale-105 hover:shadow-2xl"
                    >
                        <img 
                            :src="skill.icon" 
                            :alt="skill.name" 
                            class="w-16 h-16 sm:w-20 sm:h-20 md:w-24 md:h-24 lg:w-32 lg:h-32 mb-2 group-hover:opacity-80 transition-opacity"
                        />
                        <p class="text-white text-sm font-semibold">{{ skill.name }}</p>
                    </div>
                </div>
            </div>

            <!-- Sección de Experiencias -->
            <div>
                <h2 class="text-4xl font-bold text-white text-left mb-8 md:text-center md:mt-0 mt-8">
                    Mis Certificaciones
                </h2>
                <div class="space-y-8 py-8">
                    <div 
                        v-for="experience in Experiences" 
                        :key="experience.id" 
                        class="flex items-center rounded-xl p-4 bg-[#111a3e] shadow-lg border border-[#1f1641]"
                    >
                        <div class="w-1/4">
                            <!-- Imagen personalizada para la experiencia -->
                            <img 
                                :src="experience.customIcon || 'https://img.icons8.com/ios-filled/100/ffffff/lawyer.png'" 
                                :alt="experience.role + ' icon'" 
                                class="w-32 h-32 sm:w-24 sm:h-24 md:w-32 md:h-32 lg:w-40 lg:h-40"
                            />
                        </div>
                        <div class="w-3/4 pl-4">
                            <!-- Título del rol con enlace si existe -->
                            <h3 class="text-2xl font-semibold uppercase text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary">
                                <template v-if="experience.link">
                                    <a 
                                        :href="experience.link" 
                                        target="_blank" 
                                        rel="noopener noreferrer" 
                                        class="hover:underline"
                                    >
                                        {{ experience.role }}
                                    </a>
                                </template>
                                <template v-else>
                                    {{ experience.role }}
                                </template>
                            </h3>
                            <p class="text-white">{{ experience.company }}</p>
                            <p class="text-white">{{ experience.date }}</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue';

// Habilidades
const Skills = ref([
    { id: 1, name: 'Python', icon: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg' },
    { id: 2, name: 'JavaScript', icon: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg' },
    { id: 3, name: 'Dart', icon: 'https://www.vectorlogo.zone/logos/dartlang/dartlang-icon.svg' },
    { id: 4, name: 'HTML5', icon: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original-wordmark.svg' },
    { id: 5, name: 'CSS3', icon: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original-wordmark.svg' },
    { id: 6, name: 'Vue.js', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vuejs/vuejs-original.svg' },
    { id: 7, name: 'React Native', icon: 'https://reactnative.dev/img/header_logo.svg' },
    { id: 8, name: 'Flutter', icon: 'https://www.vectorlogo.zone/logos/flutterio/flutterio-icon.svg' },
    { id: 9, name: 'AWS Amplify', icon: 'https://docs.amplify.aws/assets/logo-dark.svg' },
    { id: 10, name: 'MongoDB', icon: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original-wordmark.svg' },
    { id: 11, name: 'PostgreSQL', icon: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original-wordmark.svg' },
    { id: 12, name: 'Docker', icon: 'https://cdn.worldvectorlogo.com/logos/docker.svg' },
]);

// Importar imágenes personalizadas
import awsIcon from '../assets/aws-academy-graduate-aws-academy-cloud-architecting.webp';
import googleIcon from '../assets/certificado-de-soporte-de-ti-de-google.webp';

// Experiencias
const Experiences = ref([
    {
        id: 1,
        role: 'AWS Academy Cloud Architecting',
        company: 'AWS Academy Graduate',
        date: '2024',
        link: 'https://www.credly.com/badges/8bd106ec-6a18-43f1-ab16-2a622da500be/public_url',
        customIcon: awsIcon,
    },
    {
        id: 2,
        role: 'Bootcamp Desarrollo Front End',
        company: 'Talento Digital-Edutecno',
        date: 'Julio 2024 - Enero 2025',
    },
    {
        id: 3,
        role: 'Google IT Support Professional Certificate',
        company: 'Google - Coursera',
        date: '2023',
        link: 'https://www.credly.com/badges/c0358dbd-21e4-4263-8ac6-24a96f5a498b/public_url',
        customIcon: googleIcon,
    },
]);
</script>

<style scoped>
/* Estilos adicionales si es necesario */
</style>
