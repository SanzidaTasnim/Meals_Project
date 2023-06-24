<template>
   <div class="flex p-8 pb-0 justify-center">
      <input 
         type="text" 
         class="rounded border-2 border-gray-200 w-[800px]" 
         placeholder="Search For Meals" 
         v-model="keyword"
         @change="searchByName"
      />
   </div>
   <div class="grid grid-cols-2 md:grid-cols-3 gap-5 p-8">
      <div v-for="meal of meals" :key="meal.idMeal" class="bg-white shadow rounded-xl">
         <router-link :to="{name: 'mealDetails' , params: {id: meal.idMeal}}">
            <img :src="meal.strMealThumb" :alt="strMeal" class="rounded-t-xl h-48 w-full object-cover" />
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
   </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import { computed } from "@vue/reactivity"
import store from '../store';
import { useRoute } from 'vue-router';
import YouTubeButton from '../components/YouTubeButton.vue';


   const keyword = ref('');
   const meals = computed(() => store.state.searchedMeals);
   const route = useRoute();

   function searchByName(){
      store.dispatch('searchMeals', keyword);
   }

   onMounted(() => {
      keyword.value = route.params.name;
      if (keyword.value) {
         searchMeals()
      }
   })
</script>
