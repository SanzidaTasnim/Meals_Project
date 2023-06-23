<template>
  <div class="bg-gray-100 h-100">
    <header class=" bg-white shadow h-20 flex justify-between items-center ">
      <router-link :to="{name: 'home'}" class="inline-flex items-center h-full px-5">
        <img class="w-14" src="./assets/logo.png" alt="Logo">
      </router-link>
      <div class="flex items-center gap-1 h-full">
        <router-link :to="{ name: 'byName'}" class="inline-flex items-center px-5 h-full hover:bg-red-200 hover:scale-105 transition-all font-semibold">
          Search Meals
        </router-link>
        <router-link :to="{ name: 'byLetter'}" class="inline-flex items-center px-5 h-full hover:bg-red-200 hover:scale-105 transition-all font-semibold">
          Meals By Letter
        </router-link>
        <router-link :to="{ name: 'byIngredient'}" class="inline-flex items-center px-5 h-full hover:bg-red-200 hover:scale-105 transition-all font-semibold">
          Meals By Ingredients
        </router-link>
      </div>
    </header>
    <main>
      <router-view />
    </main>
  </div>
</template>
<script setup>


</script>
<style scoped>

</style>
