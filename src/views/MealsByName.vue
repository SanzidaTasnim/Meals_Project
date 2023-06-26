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
   <Meals :meals="meals"/>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import { computed } from "@vue/reactivity"
import store from '../store';
import { useRoute } from 'vue-router';
import Meals from '../components/Meals.vue';


   const keyword = ref('');
   const meals = computed(() => store.state.searchedMeals);
   const route = useRoute();

   function searchByName(){
      if(keyword.value) {
         store.dispatch('searchMeals', keyword);
      } else{
         store.commit('setSearchedMeals', [] )
      }
   }

   onMounted(() => {
      keyword.value = route.params.name;
      if (keyword.value) {
         searchMeals()
      }
   })
</script>
