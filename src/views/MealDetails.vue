<template>
   <div class="max-w-[800px] mx-auto p-8">
      <h1 class="text-5xl font-bold mb-5 text-red-700 text-center">{{ meal.strMeal }}</h1>
      <img :src="meal.strMealThumb" :alt="meal.strMeal" class="w-full rounded-xl h-[500px]">
      <div class="grid grid-cols-1 sm:grid-cols-3 mt-2">
         <div>
            <strong class="font-bold">Category:</strong> {{ meal.strCategory }}
         </div>
         <div>
            <strong class="font-bold">Area:</strong> {{ meal.strArea }}
         </div>
         <div>
            <strong class="font-bold">Tags:</strong> {{ meal.strTags}}
         </div>
      </div>
      <div class="my-3 text-justify">
         {{ meal.strInstructions }}
      </div>
      <div class="grid grid-cols-1 sm:grid-cols-2 my-8">
         <div>
            <h2 class="text-2xl font-bold mb-3 text-red-700 ">Ingredients</h2>
            <ul>
               <template v-for="(i,index) of new Array(20)">
                  <li v-if="meal[`strIngredient${index + 1}`]">
                     {{ index + 1 }}.   {{ meal[`strIngredient${index + 1}`] }}
                  </li>
               </template>
            </ul>
         </div>
         <div>
            <h2 class="text-2xl text-red-700 font-bold mb-3">Measures</h2>
            <ul>
               <template v-for="(i,index) of new Array(20)">
                  <li v-if="meal[`strMeasure${index + 1}`]">
                        {{ meal[`strMeasure${index + 1}`] }}
                  </li>
               </template>
            </ul>
         </div>
         <div class="mt-12">
            <YouTubeButton :href="meal.strYoutube">
               Go To YouTube
            </YouTubeButton>
            <a :href="meal.strSource" class="px-2 py-1 rounded border-2 border-sky-600 bg-sky-500 hover:bg-sky-600 text-white transition-colors" target="_blank">
                  View Original Source
            </a>
         </div>
      </div>
   </div>
</template>
<script setup>
import { onMounted, ref } from 'vue';
import { useRoute } from 'vue-router';
import axiosClient from '../axiosClient';
import YouTubeButton from '../components/YouTubeButton.vue';

   const route = useRoute();
   const meal = ref({});
   onMounted(() => {
      const id = route.params.id;
      axiosClient.get(`lookup.php?i=${id}`)
         .then(({ data })=>{
            meal.value = data.meals[0] || {};
         })
   })

</script>