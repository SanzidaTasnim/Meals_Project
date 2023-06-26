<template>
   <header class=" bg-white shadow h-20 flex justify-between items-center ">
      <router-link :to="{name: 'home'}" class="inline-flex items-center h-full px-5">
        <img class="w-14" src="../assets/logo.png" alt="Logo">
      </router-link>
      <div class="flex items-center gap-1 h-full">
        <router-link :to="{ name: 'byName'}" class="inline-flex items-center px-5 h-full hover:bg-red-600 hover:text-white transition-all font-semibold">
          Search Meals
        </router-link>
        <router-link :to="{ name: 'byLetter'}" class="inline-flex items-center px-5 h-full hover:bg-red-600 hover:text-white transition-all font-semibold">
          Meals By Letter
        </router-link>
        <router-link :to="{ name: 'ingredients'}" class="inline-flex items-center px-5 h-full hover:bg-red-600 hover:text-white transition-all font-semibold">
          Meals By Ingredients
        </router-link>
      </div>
   </header>
</template>
<script>

</script>
