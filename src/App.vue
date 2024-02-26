<script setup>
import Calculator from './components/Calculator.vue';
import AnimeQuote from './components/AnimeQuote.vue';
</script>

<template>
  <div class="flex justify-center items-center h-screen bg-gray-100">
    <div class="grid grid-cols-1 gap-8 lg:w-[600px]">
      <Calculator />
      <AnimeQuote />
    </div>
  </div>
</template>