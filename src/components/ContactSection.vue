<template>
    <section class="text-white mt-20" id="contact">
      <!-- Título de la sección -->
      <h2 class="text-4xl font-bold text-white text-left mb-4 px-4 xl:pl-16">
        ¡Conectemos!
      </h2>
      
      <!-- Contenedor general -->
      <div 
        class="grid md:grid-cols-2 gap-4 relative px-4 xl:px-16 mt-8" 
        data-aos="zoom-in-up"
      >
        <!-- Columna Izquierda: Información de contacto -->
        <div>
          <p class="text-[#adb7be]">
            ¡Gracias por visitar mi portafolio! Si deseas ponerte en contacto para 
            hablar sobre proyectos, colaboraciones, o simplemente quieres saludar, 
            no dudes en enviarme un mensaje o utilizar mis redes profesionales.
          </p>
  
          <!-- Datos de contacto -->
          <div class="col-lg-4 col-md-4 mb-lg-0 mt-5">
            
            <!-- Email -->
            <div class="flex mb-10 items-center">
              <div 
                class="p-2"
                style="background: #111a3e; width: 50px; height: 46px; display: flex; 
                       justify-content: center; border-radius: 50%; overflow: hidden; 
                       border: 1px solid #111a3e; backdrop-filter: blur(9px); -webkit-backdrop-filter: blur(9px);"
              >
                <img 
                  src="https://img.icons8.com/metro/50/ffffff/new-post.png" 
                  alt="new-post" 
                  class="w-6"
                />
              </div>
              <div class="ml-5 text-white">
                <h4>Correo</h4>
                <p>hernan.espinoza.dev@gmail.com</p>
              </div>
            </div>
  
            <!-- LinkedIn -->
            <div class="flex mb-10 items-center">
              <div 
                class="p-2"
                style="background: #111a3e; width: 50px; height: 46px; display: flex; 
                       justify-content: center; border-radius: 50%; overflow: hidden; 
                       border: 1px solid #111a3e; backdrop-filter: blur(9px); -webkit-backdrop-filter: blur(9px);"
              >
                <img 
                  src="https://img.icons8.com/ios-filled/50/ffffff/linkedin.png" 
                  alt="linkedin"
                  class="w-6"
                />
              </div>
              <div class="ml-5 text-white">
                <h4>LinkedIn</h4>
                <p>
                  <a 
                    href="https://www.linkedin.com/in/hernanespinozadev/" 
                    target="_blank" 
                    rel="noopener noreferrer"
                    class="hover:underline"
                  >
                    hernanespinozadev
                  </a>
                </p>
              </div>
            </div>
  
            <!-- GitHub -->
            <div class="flex items-center">
              <div 
                class="p-2"
                style="background: #111a3e; width: 50px; height: 46px; display: flex; 
                       justify-content: center; border-radius: 50%; overflow: hidden; 
                       border: 1px solid #111a3e; backdrop-filter: blur(9px); -webkit-backdrop-filter: blur(9px);"
              >
                <!-- Ícono de GitHub -->
                <img 
                  src="https://img.icons8.com/ios-glyphs/60/ffffff/github.png" 
                  alt="github"
                  class="w-6"
                />
              </div>
              <div class="ml-5 text-white">
                <h4>GitHub</h4>
                <p>
                  <a 
                    href="https://github.com/HernanEspinozaDev"
                    target="_blank" 
                    rel="noopener noreferrer"
                    class="hover:underline"
                  >
                    HernanEspinozaDev
                  </a>
                </p>
              </div>
            </div>
  
          </div>
        </div>
  
        <!-- Columna Derecha: Formulario de Contacto -->
        <div
          style="background: #111a3e; width: 100%; height: 100%; border-radius: 20px;
                 overflow: hidden; border: 1px solid #111a3e; backdrop-filter: blur(9px); 
                 -webkit-backdrop-filter: blur(9px);"
        >
          <!-- IMPORTANTE: @submit.prevent="sendEmail" -->
          <form class="flex flex-col p-2" data-aos="zoom-in-up" @submit.prevent="sendEmail">
            <!-- Email -->
            <div class="mb-6">
              <label for="email" class="text-white block mb-2 text-sm font-medium">
                Correo Electrónico
              </label>
              <input 
                v-model="formData.email"
                type="email" 
                id="email" 
                class="bg-[#111827] placeholder:[#9CA2A9] text-gray-100 text-sm 
                       rounded-lg block w-full p-2.5"
                placeholder="tucorreo@example.com" 
                name="email"
                required
              />
            </div>
  
            <!-- Asunto -->
            <div class="mb-6">
              <label for="subject" class="text-white block mb-2 text-sm font-medium">
                Asunto
              </label>
              <input 
                v-model="formData.subject"
                type="text" 
                id="subject" 
                class="bg-[#111827] placeholder:[#9CA2A9] text-gray-100 text-sm 
                       rounded-lg block w-full p-2.5"
                placeholder="Asunto" 
                name="subject"
                required
              />
            </div>
  
            <!-- Mensaje -->
            <div class="mb-6">
              <label for="message" class="text-white block mb-2 text-sm font-medium">
                Mensaje
              </label>
              <textarea 
                v-model="formData.message"
                id="message" 
                class="bg-[#111827] placeholder:[#9CA2A9] text-gray-100 text-sm 
                       rounded-lg block w-full p-2.5"
                placeholder="Escribe tu mensaje aquí..."
                name="message"
                required
              ></textarea>
            </div>
  
            <!-- Botón de envío -->
            <button 
              class="z-1 w-full px-6 md:px-7 py-3 rounded-full 
                     flex justify-center text-white bg-primary 
                     border-2 border-transparent hover:bg-opacity-90 
                     transition-colors"
            >
              Enviar Mensaje
            </button>
          </form>
        </div>
  
        <!-- Efecto decorativo (gradiente) -->
        <div 
          class="bg-gradient-to-tr opacity-25 from-[#570cac] to-primary blur-2xl h-20 w-80 
                 z-0 absolute -top-1/2 -left-4 transform -translate-x-2/3 -translate-1/2"
        ></div>
      </div>
  
      <!-- MODAL DE CONFIRMACIÓN -->
      <div 
        v-if="showModal" 
        class="fixed inset-0 flex items-center justify-center z-50"
      >
        <!-- Fondo oscuro semi-transparente -->
        <div 
          class="absolute inset-0 bg-black bg-opacity-50" 
          @click="showModal = false"
        ></div>
        
        <!-- Contenido del modal -->
        <div 
          class="relative bg-[#111a3e] border border-[#1f1641] 
                 rounded-xl p-6 w-11/12 max-w-sm mx-auto z-10"
          style="backdrop-filter: blur(9px); -webkit-backdrop-filter: blur(9px);"
        >
          <!-- Ícono check -->
          <div class="flex items-center justify-center mb-4">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="2"
              stroke="currentColor"
              class="h-10 w-10 text-green-400"
            >
              <path 
                stroke-linecap="round" 
                stroke-linejoin="round" 
                d="M4.5 12.75l6 6 9-13.5" 
              />
            </svg>
          </div>
  
          <!-- Mensaje de confirmación -->
          <p class="text-white text-center mb-6">
            ¡Mensaje enviado! Pronto me pondré en contacto contigo.
          </p>
  
          <!-- Botón "Aceptar" -->
          <button
            class="block mx-auto px-6 py-2 text-white bg-primary 
                   hover:bg-opacity-90 rounded-full"
            @click="showModal = false"
          >
            Aceptar
          </button>
        </div>
      </div>
    </section>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  import emailjs from '@emailjs/browser'
  
  // Datos del formulario
  const formData = ref({
    email: '',
    subject: '',
    message: ''
  })
  
  // Variable para mostrar/ocultar el modal
  const showModal = ref(false)
  
  // Función para enviar el correo usando EmailJS
  const sendEmail = () => {
    emailjs
      .send(
        'service_jz7s5ho',    // Service ID
        'template_ihwi1dp',   // Template ID
        {
          from_email: formData.value.email,
          subject: formData.value.subject,
          message: formData.value.message
        },
        'Of57a4GRk-uRxt6OM'   // Public Key
      )
      .then(
        (response) => {
          console.log('¡Correo enviado con éxito!', response.status, response.text)
          // Mostramos el modal en lugar de alert
          showModal.value = true
  
          // Limpiamos campos
          formData.value.email = ''
          formData.value.subject = ''
          formData.value.message = ''
        },
        (error) => {
          console.error('Error al enviar el correo:', error)
          alert('Ocurrió un error al enviar tu mensaje. Por favor, inténtalo más tarde.')
        }
      )
  }
  </script>
  
  <style scoped>
  /* Estilos adicionales (opcionales) */
  </style>
  