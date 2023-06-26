<template>
   <div class="grid grid-cols-1 md:grid-cols-3 gap-5 px-8">
      <MealItem  v-for="meal of meals" :key="meal.idMeal" :meal="meal"/>
   </div>
   <div v-if="!meals.length" class="flex justify-center text-gray-700 p-2 h-[400px] items-center text-2xl ">
      <h2>There Are No Meals</h2>
   </div>
</template>
<script setup>
import MealItem from './MealItem.vue';
const { meals } = defineProps({
   meals: {
      required: true,
      type: Array
   }
})

</script>