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
                            <button 
                                v-if="element.certificateUrl"
                                @click="openCertificateModal(element)"
                                class="text-2xl font-semibold uppercase text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary lg:text-xl hover:opacity-80 transition-opacity text-left w-full"
                            >
                                {{ element.program }}
                            </button>
                            <h3 v-else class="text-2xl font-semibold uppercase text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary lg:text-xl">
                                {{ element.program }}
                            </h3>
                            <p class="text-white">{{ element.School }}</p>
                            <p class="text-white">{{ element.year }}</p>
                            <p class="text-gray-400 text-sm" v-if="element.status">{{ element.status }}</p>
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
                    Más de 10 años de experiencia en reparación electrónica de celulares, mantenimiento de hardware y software.<br><br>
                    Programador junior especializado en Python, desarrollo web y desarrollo móvil con React Native, Flutter.
                </p>
                    
            </div>
        </div>
    </section>

    <!-- Certificate Modal -->
    <Teleport to="body" v-if="showCertificateModal">
        <div 
            class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50 p-4"
            @click.self="closeCertificateModal"
        >
            <div class="bg-gray-900 rounded-lg shadow-2xl w-full max-w-4xl max-h-[90vh] flex flex-col">
                <!-- Header -->
                <div class="flex items-center justify-between p-4 sm:p-6 border-b border-gray-700">
                    <h2 class="text-white text-lg sm:text-xl font-semibold">{{ currentCertificate.program }}</h2>
                    <div class="flex items-center gap-3">
                        <button 
                            @click="downloadCertificate"
                            class="bg-primary text-white px-4 py-2 rounded hover:bg-primary/80 transition-colors text-sm sm:text-base"
                        >
                            Descargar
                        </button>
                        <button 
                            @click="closeCertificateModal"
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
                        :src="currentCertificate.certificateUrl"
                        class="w-full h-full min-h-[500px]"
                        :title="currentCertificate.program"
                    ></iframe>
                </div>
            </div>
        </div>
    </Teleport>
</template>

<script setup>
import { ref } from 'vue';
import tnmElectronica from '../assets/tnmelectronica.pdf';
import tnsAnalistaProgramador from '../assets/tnsanalistaprogramador.pdf';

// Información de la educación
const education = ref([
    {
        id: 1,
        School: 'Escuela Industrial de San Antonio',
        program: 'Técnico de Nivel Medio en Electrónica',
        year: 'Marzo 2008 – Diciembre 2011',
        status: 'Titulado',
        certificateUrl: tnmElectronica,
    },
    {
        id: 2,
        School: 'INACAP Santiago Centro',
        program: 'Técnico de Nivel Superior Analista Programador',
        year: 'Marzo 2023 – Diciembre 2024',
        status: 'Titulado',
        certificateUrl: tnsAnalistaProgramador,
    },
    {
        id: 3,
        School: 'INACAP Santiago Centro',
        program: 'Ingeniería en Informática',
        year: '2025 – 2026',
        status: 'En curso (Egreso previsto: julio 2026)',
        certificateUrl: null,
    }
]);

const showCertificateModal = ref(false);
const currentCertificate = ref({
    program: '',
    certificateUrl: '',
});

const openCertificateModal = (element) => {
    currentCertificate.value = {
        program: element.program,
        certificateUrl: element.certificateUrl,
    };
    showCertificateModal.value = true;
    document.body.style.overflow = 'hidden';
};

const closeCertificateModal = () => {
    showCertificateModal.value = false;
    document.body.style.overflow = 'auto';
};

const downloadCertificate = () => {
    const link = document.createElement('a');
    link.href = currentCertificate.value.certificateUrl;
    link.download = `${currentCertificate.value.program}.pdf`;
    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);
};
</script>
