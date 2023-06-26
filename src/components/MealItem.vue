<template>
   <div class="bg-white shadow rounded-xl">
         <router-link :to="{name: 'mealDetails' , params: {id: meal.idMeal}}">
            <img 
               :src="meal.strMealThumb" 
               :alt="meal.strMeal" 
               class="rounded-t-xl h-48 w-full object-cover" 
            />
         </router-link>
         <div class="p-3">
            <h3 class="font-bold">{{ meal.strMeal }}</h3>
            <p class="mb-4">
               Lorem ipsum dolor sit amet consectetur adipisicing elit. Fuga omnis a ipsa, dolor numquam necessitatibus!
            </p>
            <div class="flex items-center justify-between">
               <YouTubeButton :href="meal.strYoutube">
                  You Tube
               </YouTubeButton>
               <router-link :to="{name: 'mealDetails' , params: {id: meal.idMeal}}" class="px-2 py-1 rounded border-2 border-sky-600 bg-sky-500 hover:bg-sky-600 text-white transition-colors">
                  View
               </router-link>
            </div>
         </div>
      </div>
</template>

<script setup>
   import YouTubeButton from './YouTubeButton.vue';
   const { meal } = defineProps({
      meal: Object
   })
</script>