<template>
   <div class="flex gap-2 justify-center mt-2 pb-2">
      <router-link :to="{ name: 'byLetter', params: {letter} }" :key="letter" v-for="letter in letters" class="bg-orange-700 py-2 px-3 rounded text-white hover:scale-110 transition-all font-semibold">
         {{ letter }}
      </router-link>
   </div>
   <Meals :meals="meals" />
</template>

<script setup>
import { onMounted, watch } from 'vue';
import { computed } from '@vue/reactivity';
import store from '../store';
import { useRoute } from 'vue-router';
import Meals from './../components/Meals.vue';

   const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ".split('');
   const meals = computed(() => store.state.mealsByLetter);
   const route = useRoute();
   
   watch(route, () => {
      store.dispatch('searchMealsByLetter', route.params.letter);
   })
   onMounted(() => {
      store.dispatch('searchMealsByLetter', route.params.letter)
   })
</script>
