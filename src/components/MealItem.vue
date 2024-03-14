<template>
  <div class="bg-white shadow rounded-x1">
    <router-link :to="{ name: 'mealDetails', params: { id: meal.idMeal } }">
      <img :src="meal.strMealThumb" :alt="meal.strMeal" class="rounded-t-2xl" />
      <h3 class="p-3 font-semibold">{{ meal.strMeal }}</h3>
      <p class="mb-4 p-3">{{ meal.strInstructions }}</p>
    </router-link>
    <div class="p-3 flex items-center justify-between">
      <YoutubeButton :href="meal.strYoutube">Youtube</YoutubeButton>
    </div>
  </div>
</template>

<script setup>
import YoutubeButton from "./YoutubeButton.vue";

const { meal } = defineProps({
  meal: {
    type: Object,
    required: true,
  },
});
</script>
