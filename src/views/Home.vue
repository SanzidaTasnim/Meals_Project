<template>
   <div class="flex p-8 justify-center">
      <input type="text" class="rounded border-2 border-gray-200 w-[800px]" placeholder="Search For Meals" >
   </div>
   <div class="flex gap-2 justify-center mt-2 ">
      <router-link :to="{ name: 'byLetter', params: {letter} }" :key="letter" v-for="letter in letters" class="bg-orange-700 py-2 px-3 rounded text-white hover:scale-110 transition-all font-semibold">
         {{ letter }}
      </router-link>
   </div>
   <div>
      <pre>
         {{ ingredients }}
      </pre>
   </div>
</template>

<script setup>
   import {onMounted, ref } from 'vue';
   import axiosClient from '../axiosClient.js';
   const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ".split('');
   const ingredients = ref([]);

   onMounted(async () => {
      const response = await axiosClient.get('list.php?i=list');
      ingredients.value = response.data;
   })
</script>