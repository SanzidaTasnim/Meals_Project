<template>
   <a 
      :href="href" 
      target="_blank" 
      class="px-2 py-1 rounded border-2 border-red-600 bg-red-500 hover:bg-red-600 text-white transition-colors mr-4">

      <slot></slot>
   </a>
</template>
<script setup>
   const props = defineProps({
      href: String
   })
</script>