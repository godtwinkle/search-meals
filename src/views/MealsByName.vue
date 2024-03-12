<template>
  <div class="p-8">
    <input
      type="text"
      class="rounded border-2 border-gray-200 w-full"
      placeholder="Tìm kiếm món ăn"
      v-model="keyword"
      @change="searchMeals"
    />
  </div>
  >
</template>

<script setup>
import { ref } from "vue";
const keyword = "";

function searchMeals() {}
</script>
