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
                        <a 
                            href="https://drive.google.com/file/d/1UdUm1_MlxNrgh7jqvUFVMPF1gcugmDzc/view?usp=sharing" 
                            target="_blank" 
                            download="Hernán_Espinoza_-_Analista_Programador.pdf" 
                            class="border border-primary px-6 md:px-7 py-3 rounded-full relative group w-full sm:w-max flex justify-center text-primary hover:scale-105 transition-all ease-in-out"
                        >
                            Descargar CV
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import AOS from 'aos';
import 'aos/dist/aos.css';
AOS.init();

const scrollToSection = (href) => {
    const section = document.querySelector(href);
    if (section) {
        section.scrollIntoView({ behavior: 'smooth' });
    }
};
</script>
