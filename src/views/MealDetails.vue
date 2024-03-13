<template>
  <div class="max-w-[800px] mx-auto p-8">
    <h1 class="text-5xl font-bold mb-5">{{ meal.strMeal }}</h1>
    <img :src="meal.strMealThumb" :alt="meal.strMeal" class="max-w-[100%]" />
    <div class="grid grid-cols-1 sm:grid-cols-3 text-lg py-2">
      <div><strong class="font-bold">Loại: </strong>{{ meal.strCategory }}</div>
      <div><strong class="font-bold">Khu vực: </strong>{{ meal.strArea }}</div>
      <div><strong class="font-bold">Nhãn: </strong>{{ meal.strTags }}</div>
    </div>

    <div class="my-3">
      {{ meal.strInstructions }}
    </div>

    <div class="grid grid-cols-1 sm:grid-cols-2">
      <div>
        <h2 class="text-2xl font-semibold mb-2">Thành phần</h2>
        <ul>
          <template v-for="(el, ind) of new Array(20)">
            <li
              v-if="meal[`strIngredient${ind + 1}`]"
              :key="meal[`strIngredient${ind + 1}`]"
            >
              {{ meal[`strIngredient${ind + 1}`] }}
            </li>
          </template>
        </ul>
      </div>
      <div>
        <h2 class="text-2xl font-semibold mb-2">Hàm lượng</h2>
        <ul>
          <template v-for="(el, ind) of new Array(20)">
            <li
              v-if="meal[`strMeasure${ind + 1}`]"
              :key="meal[`strMeasure${ind + 1}`]"
            >
              {{ meal[`strMeasure${ind + 1}`] }}
            </li>
          </template>
        </ul>
      </div>
    </div>
    <div class="mt-4">
      <YoutubeButton :href="meal.strYoutube">Youtube</YoutubeButton>
      <a
        :href="meal.strSource"
        target="_blank"
        class="ml-3 px-3 py-2 rounded border-2 border-transparent bg-indigo-500 hover:bg-indigo-600 text-white transition-colors"
      >
        Xem
      </a>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue";
import { useRoute } from "vue-router";
import axiosClient from "../axiosClient";
import YoutubeButton from "./YoutubeButton.vue";

const route = useRoute();
const meal = ref({});

onMounted(() => {
  axiosClient.get(`lookup.php?i=${route.params.id}`).then(({ data }) => {
    meal.value = data.meals[0] || {};
  });
});
</script>
