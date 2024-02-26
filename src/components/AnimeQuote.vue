<script setup>
import { ref, reactive, onMounted } from "vue";
import axios from "axios";

const data = reactive([])
const isLoading = ref(false);

onMounted(() => {
  isLoading.value = true;
  ApiFetch();
});

const ApiFetch = () => {
  axios.get('https://animechan.xyz/api/random')
  .then((res) => {
    Object.assign(data, res.data)
    isLoading.value = false;
  })
  .catch((error) => {
    console.log(error)
    isLoading.value = false;
  })
}
</script>

<template>
  <div class="bg-white p-8 rounded-lg shadow-lg">
    <h1 class="text-3xl font-semibold mb-4">Random Anime Quote</h1>
    <div v-if="isLoading" class="text-center text-gray-600">Loading...</div>
    <div v-else-if="data.quote" class="space-y-4">
      <div class="text-lg">
        <span class="font-semibold">Id:</span> {{ data.id }}
      </div>
      <div class="text-lg">
        <span class="font-semibold">Quote:</span> {{ data.quote }}
      </div>
      <div class="text-lg">
        <span class="font-semibold">Anime:</span> {{ data.anime }}
      </div>
      <div class="text-lg">
        <span class="font-semibold">Character:</span> {{ data.character }}
      </div>
    </div>
    <div v-else class="text-red-500">Failed to fetch data.</div>
  </div>
</template>
