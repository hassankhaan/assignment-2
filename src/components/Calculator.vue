<script setup>
import { ref } from "vue";

const num1 = ref(0);
const num2 = ref(0);
const operator = ref("add");
const result = ref(null);

const calculate = () => {
    if(operator.value == 'add'){
        result.value = num1.value + num2.value;
    }
    else if(operator.value == 'subtract'){
        result.value = num1.value - num2.value;
    }
    else if(operator.value == 'multiply'){
        result.value = num1.value * num2.value;
    }
    else if(operator.value == 'divide'){
        if (num2.value !== 0) {
            result.value = num1.value / num2.value;
        } else {
            result.value = "Error: Division by zero";
        }
    }
};
</script>

<template>
  <div class="bg-white p-8 rounded-lg shadow-lg">
    <h1 class="text-3xl font-semibold mb-4">Simple Calculator</h1>
    <div class="flex flex-col space-y-4">
      <div class="flex space-x-4 items-center">
        <input
          v-model="num1"
          type="number"
          class="p-2 border border-gray-300 rounded-lg flex-1"
          placeholder="Enter number"
        />
        <select
          v-model="operator"
          class="p-2 border border-gray-300 rounded-lg w-20"
        >
          <option value="add">+</option>
          <option value="subtract">-</option>
          <option value="multiply">*</option>
          <option value="divide">/</option>
        </select>
        <input
          v-model="num2"
          type="number"
          class="p-2 border border-gray-300 rounded-lg flex-1"
          placeholder="Enter number"
        />
      </div>
      <button
        @click="calculate"
        class="px-4 py-2 bg-blue-500 text-white rounded-lg w-full"
      >
        Calculate
      </button>
      <div v-if="result !== null" class="text-2xl font-bold text-center">
        {{ result }}
      </div>
    </div>
  </div>
</template>
