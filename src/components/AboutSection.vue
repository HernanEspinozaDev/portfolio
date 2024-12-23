<template>
    <section class="text-white mt-18" id="about">
        <div class="absolute z-0 top-[93rem] inset-x-0 h-64 flex items-start">
            <div class="h-24 w-64 bg-gradient-to-br from-primary via-secondary blur-2xl to-[#570cac] opacity-20"></div>
        </div>
        <div class="md:grid md:grid-cols-2 gap-8 items-center py-8 px-4 xl:gap-16 sm:py-16 xl:px-16 z-1">
            <div data-aos="flip-right">
                <h2 class="text-4xl font-bold text-white text-left mb-8">Mi Educación</h2>
                <div class="space-y-8 py-8">
                    <div v-for="element in education" :key="element.id"
                        class="flex items-center md:w-[80%] w-full rounded-xl bg-[#111a3e] shadow-lg border border-[#1f1641]">
                        <div class="w-1/4">
                            <img src="https://img.icons8.com/ios-glyphs/60/ffffff/graduation-cap--v1.png" alt="graduation-cap">
                        </div>
                        <div class="w-3/4 pl-4">
                            <h3 class="text-2xl font-semibold uppercase text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary lg:text-xl">
                                {{ element.School }}
                            </h3>
                            <p class="text-white">{{ element.program }}</p>
                            <p class="text-white">{{ element.year }}</p>
                        </div>
                    </div>
                </div>
            </div>
            <div class="mt-4 md:mt-0 text-left flex flex-col z-10 h-full" data-aos="flip-right">
                <h2 class="text-4xl font-bold text-white md:text-center text-left mb-4">Más 
                    <span class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary">Sobre Mí</span>
                </h2>
                <p class="text-base lg:text-lg mt-8 py-8">
                    Apasionado por la robótica, la electrónica y la programación.<br><br>
                    Más de 8 años de experiencia en reparación electrónica de celulares, mantenimiento de hardware y software.<br><br>
                    Programador junior especializado en Python, desarrollo web y desarrollo móvil con React Native, Flutter.
                </p>
                    
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue';

// Información de la educación
const education = ref([
    {
        id: 1,
        School: 'INACAP Santiago Centro',
        program: 'Analista Programador',
        year: 'Mar 2023 – Dic 2024',
    }
]);
</script>
