<template>
    <section class="relative w-full" data-aos="zoom-in-up">
        <div class="absolute top-0 inset-x-0 h-64 flex items-start">
            <div class="h-24 w-2/3 bg-gradient-to-br from-[#570cac] blur-2xl invisible opacity-40"></div>
            <div class="h-20 w-3/5 bg-gradient-to-r from-[#670ccf] opacity-40 blur-2xl"></div>
        </div>
        <div class="w-full px-5 sm:px-8 md:px-12 lg:px-8 max-w-screen-lg lg:max-w-screen-xl mx-auto relative">
            <div class="grid gap-10 xl:gap-14 relative pt-24 max-w-2xl md:max-w-3xl mx-auto">
                <div class="py-6 text-center">
                    <h1 class="pt-4 text-white font-bold text-4xl md:text-5xl lg:text-6xl">
                        Hola, soy <span class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-pink-500">
                            Hernán Espinoza
                        </span> 😁
                    </h1>
                    <p class="text-gray-300 pt-8 mx-auto max-w-xl">
                        Analista Programador, desarrollador web fullstack y móvil.<br>
                        Con experiencia práctica demostrable en Python, React Native, desarrollo web y AWS.
                    </p>

                    <div class="flex items-center justify-center gap-3 pt-9 flex-col sm:flex-row">
                        <button 
                            @click="scrollToSection('#contact')" 
                            class="px-6 md:px-7 py-3 rounded-full relative group w-full sm:w-max flex justify-center">
                            <span class="absolute inset-0 rounded-3xl group-hover:scale-105 origin-center transition-all ease-in-out bg-primary border-2 border-transparent"></span>
                            <span class="relative flex items-center justify-center text-white">Contáctame</span>
                        </button>
                        <button 
                            @click="openCVModal"
                            class="border border-primary px-6 md:px-7 py-3 rounded-full relative group w-full sm:w-max flex justify-center text-primary hover:scale-105 transition-all ease-in-out"
                        >
                            Descargar CV
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- CV Modal -->
    <Teleport to="body" v-if="showCVModal">
        <div 
            class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50 p-4"
            @click.self="closeCVModal"
        >
            <div class="bg-gray-900 rounded-lg shadow-2xl w-full max-w-4xl max-h-[90vh] flex flex-col">
                <!-- Header -->
                <div class="flex items-center justify-between p-4 sm:p-6 border-b border-gray-700">
                    <h2 class="text-white text-lg sm:text-xl font-semibold">Mi CV</h2>
                    <div class="flex items-center gap-3">
                        <button 
                            @click="downloadCV"
                            class="bg-primary text-white px-4 py-2 rounded hover:bg-primary/80 transition-colors text-sm sm:text-base"
                        >
                            Descargar
                        </button>
                        <button 
                            @click="closeCVModal"
                            class="text-gray-400 hover:text-white text-2xl transition-colors"
                            aria-label="Cerrar modal"
                        >
                            ×
                        </button>
                    </div>
                </div>
                
                <!-- PDF Container -->
                <div class="flex-1 overflow-auto">
                    <iframe 
                        :src="cvPdfUrl"
                        class="w-full h-full min-h-[500px]"
                        title="CV Hernán Espinoza"
                    ></iframe>
                </div>
            </div>
        </div>
    </Teleport>
</template>

<script setup>
import { ref } from 'vue';
import AOS from 'aos';
import 'aos/dist/aos.css';

AOS.init();

const showCVModal = ref(false);
const cvPdfUrl = new URL('../assets/CV Hernán Espinoza Ing. Informática.pdf', import.meta.url).href;

const scrollToSection = (href) => {
    const section = document.querySelector(href);
    if (section) {
        section.scrollIntoView({ behavior: 'smooth' });
    }
};

const openCVModal = () => {
    showCVModal.value = true;
    document.body.style.overflow = 'hidden';
};

const closeCVModal = () => {
    showCVModal.value = false;
    document.body.style.overflow = 'auto';
};

const downloadCV = () => {
    const link = document.createElement('a');
    link.href = cvPdfUrl;
    link.download = 'Hernán_Espinoza_-_Analista_Programador.pdf';
    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);
};
</script>
