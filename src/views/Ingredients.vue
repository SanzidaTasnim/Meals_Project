<template>
   <div class="p-8">
      <h1 class="text-4xl font-bold text-red-600 mb-8">Ingredients</h1>
      <input 
         type="text" 
         class="rounded border-2 mb-3 border-gray-200 w-[800px]" 
         placeholder="Search For Ingredients" 
         v-model="keyword"
      />
      <router-link 
         :to="{
            name: 'byIngredient', 
            params: {ingredient: ingredient.strIngredient}}" 
         v-for="ingredient of computedIngredients" :key="ingredient.id" 
         class="block bg-white rounded p-3 mb-3 shadow">
         
         <h3 class="text-2xl font-bold mb-2"> {{ ingredient.strIngredient }}</h3>
         <p>{{ ingredient.strDescription }}</p>
         
      </router-link>
   </div>
</template>

<script setup>
import { computed } from "@vue/reactivity";
import { onMounted, ref } from 'vue';
import axiosClient from '../axiosClient';

   const ingredients = ref([]);
   const keyword= ref('');
   const computedIngredients = computed(() => {
      if(!computedIngredients) return ingredients;

      return ingredients.value.filter(i =>
      i.strIngredient.toLowerCase().includes(keyword.value.toLowerCase())
      )
   })
   onMounted(() => {
      axiosClient.get('list.php?i=list')
         .then(({ data }) => {
            ingredients.value = data.meals;
         })
   })
</script> 
