<template>
    <section class="text-white mt-20" id="services">
        <div class="px-4 xl:pl-16">
            <h2 class="text-4xl font-bold text-white mb-4">Mis Servicios</h2>
        </div>
        <div class="py-8 xl:px-16 px-4 sm:py-16 grid grid-cols-1 gap-6 pt-10 sm:grid-cols-2 md:gap-10 md:pt-12 lg:grid-cols-3">
            <div 
                v-for="service in services" 
                :key="service.id" 
                data-aos="fade-up"
                class="px-8 py-12 rounded-xl bg-[#111a3e] shadow-lg border border-[#1f1641]"
            >
                <div class="mx-auto h-24 w-24 text-center xl:h-28 xl:w-28">
                    <div>
                        <img :src="service.icon" :alt="`Icono de ${service.name}`">
                    </div>
                </div>
                <div class="text-center">
                    <h3 class="pt-8 text-lg font-semibold uppercase text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary lg:text-xl">
                        {{ service.name }}
                    </h3>
                    <p class="text-grey pt-4 text-sm group-hover:text-white md:text-base">
                        {{ service.description }}
                    </p>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue';

const services = ref([
    {
        id: 1,
        icon: 'https://img.icons8.com/ios-filled/100/ffffff/google-code.png',
        name: 'Desarrollo Web',
        description: 'Desarrollo páginas web responsivas, desde lo más básico: páginas estáticas hasta dinámicas con bases de datos o conexiones API.'
    },
    {
        id: 2,
        icon: 'https://img.icons8.com/external-vectorslab-glyph-vectorslab/100/fffeee/external-Technical-Writing-mobile-app-development-vectorslab-glyph-vectorslab.png',
        name: 'Soporte de Software',
        description: 'Mejora y mantenimiento a tu software para asegurar su óptimo funcionamiento.'
    },
    {
        id: 3,
        icon: 'https://img.icons8.com/external-solid-design-circle/100/ffffff/external-Mobile-Development-digital-marketing-solid-design-circle.png',
        name: 'Desarrollo de Aplicaciones Móviles',
        description: 'Desarrollo aplicaciones móviles a medida para satisfacer las necesidades específicas de tu negocio.'
    },
    {
        id: 4,
        icon: 'https://img.icons8.com/ios-filled/100/ffffff/email-open.png',
        name: 'Web Empresarial',
        description: 'Implemento soluciones empresariales como correos corporativos, gestión de trabajadores y más.'
    },
    {
        id: 5,
        icon: 'https://img.icons8.com/ios-filled/100/ffffff/windows10-personalization.png',
        name: 'Diseño de la Web',
        description: 'Mejoro el diseño de tu sitio web para hacerlo más atractivo y funcional.'
    },
    {
        id: 6,
        icon: 'https://img.icons8.com/ios-filled/100/ffffff/web-design.png',
        name: 'Página Web para Pyme',
        description: 'Creo páginas web con chatbots y otras funcionalidades para mejorar el alcance de tu emprendimiento.'
    },
]);
</script>

<style scoped>
/* Puedes agregar estilos adicionales aquí si lo deseas */
</style>
