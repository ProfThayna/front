<template>
    <div class="max-w-2xl mx-auto p-6 bg-white shadow-lg rounded-lg flex justify-between">
      <!-- Professional Info Section -->
      <img src="image.png"
        alt="Profile Picture"
        class="rounded-full w-12 h-12 object-cover absolute top-0 left-0 mt-4 ml-4">
      <div class="flex flex-col justify-start">
        <div class="flex items-center space-x-4">
          <div class="rounded-full h-12 w-12 bg-gray-300"></div>
          <div>
            <h2 class="text-xl font-semibold text-cyan-300">Anna Castro</h2>
            <p class="text-gray-500">PSICOLOGA | São Paulo</p>
          </div>
        </div>
        <div class="mt-3">
          <p class="text-gray-700 text-sm">Formada pela Universidade de São Paulo (USP) em 2020. Com vasta experiência no campo da saúde mental, busco oferecer um cuidado compassivo e individualizado aos meus pacientes. Focando no tratamento de transtornos mentais, ansiedade, depressão e estresse pós-traumático. Busco sempre estar atualizada com as mais recentes pesquisas e terapias, meu objetivo e ajudar voce a alcançarem uma saúde mental plena e equilibrada.</p>
        </div>
        <div class="mt-4">
          <span class="text-gray-500 text-sm">(20 reviews)</span>
          <span class="block text-lg font-semibold">R$100 / 50 minutos</span>
        </div>
      </div>
      
      <!-- Schedule Section -->
      <div class="mt-6">
      <div class="flex justify-between">
      <!-- Days of the week -->
       <div v-for="day in days" :key="day.date" class="flex flex-col items-center">
         <div class="font-bold">{{ day.date }}</div>
         <div class="flex flex-col">
         <!-- Time slots for each day -->
           <div v-for="time in day.slots" :key="time" class="my-2 p-2 border rounded-lg text-center cursor-pointer hover:bg-blue-500 hover:text-white">
                {{ time }}
           </div>
         </div>
         </div>
       </div>
    </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';

  export default {
    data() {
      return {
         days: [], // Will be populated with data from the server
      };
    },
    mounted() {
      this.fetchAvailableSlots();
    },
    methods: {
      fetchAvailableSlots() {
      // Replace with your actual API endpoint
       axios.get('http://localhost:3000/slots')
        .then(response => {
          this.days = response.data;
        })
        .catch(error => {
            // eslint-disable-next-line no-console
          console.error("There was an error fetching the slots:", error);
        });
       }
    },
  };
  </script>
  