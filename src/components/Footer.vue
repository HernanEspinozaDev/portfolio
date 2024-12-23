<template>
    <footer 
      class="mt-8 border-t border-[#33353F] text-white z-10 bg-[#111a3e]"
      style="backdrop-filter: blur(9px); -webkit-backdrop-filter: blur(9px);"
    >
      <div 
        class="p-6 flex flex-col md:flex-row items-center justify-between max-w-7xl mx-auto"
      >
        <!-- LOGO + Enlace -->
        <a 
          href="https://hotusoft.com" 
          target="_blank" 
          rel="noopener noreferrer"
          class="flex items-center space-x-2 mb-4 md:mb-0"
        >
          <!-- Logo de HotuSoft -->
          <img 
            src="../assets/HotuSoft-Logo-Large.webp" 
            alt="HotuSoft Logo" 
            class="h-10 object-contain"
          />
        </a>
  
        <!-- Texto con margen derecho -->
        <p class="text-sm md:text-base text-gray-400 flex items-center mr-8">
          <!-- Ícono “©” en SVG -->
          <svg 
            xmlns="http://www.w3.org/2000/svg" 
            fill="currentColor" 
            viewBox="0 0 16 16"
            class="w-4 h-4 text-gray-400 mr-1"
          >
            <path 
              d="M8 1.333A6.667 6.667 0 1 0 8 14.667 6.667 6.667 0 0 0 8 1.333zm0 12A5.333 5.333 0 1 1 8 2.667 5.333 5.333 0 0 1 8 13.333zm0-8A2.667 2.667 0 1 0 8 10a2.667 2.667 0 0 0 0-5.333z" 
            />
          </svg>
          <span>
            Created by 
            <strong class="text-white"> HotuSoft</strong> – 
            <strong class="text-white">HernanEspinozaDev</strong>.<br> 
            All rights reserved 2024.
          </span>
        </p>
      </div>
    </footer>
  </template>
  
  <script>
  export default {
    name: 'FooterComponent'
  }
  </script>
  
  <style scoped>
  /* Ajustes opcionales, por ejemplo, si deseas un hover al logo */
  a:hover img {
    opacity: 0.9;
    transition: opacity 0.3s;
  }
  </style>
  