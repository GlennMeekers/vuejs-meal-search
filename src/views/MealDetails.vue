<template>
  <div class="w-[800px] mx-auto p-8">
    <!-- <pre>{{ meal }}</pre> -->
    <h3 class="text-5xl font-bold mb-5">{{ meal.strMeal }}</h3>
    <img :src="meal.strMealThumb" :alt="meal.strMeal" />
    <div class="inline-grid grid-cols-1 md:grid-cols-3 text-lg py-2">
      <div><strong>Category:</strong> {{ meal.strCategory }}</div>
      <div><strong>Area:</strong> {{ meal.strArea }}</div>
      <div>
        <strong>Tags:</strong>
        {{ meal.strTags }}
      </div>
    </div>

    <div class="my-3">
      {{ meal.strInstructions }}
    </div>

    <div class="grid grid-cols-1 sm:grid-cols-2">
      <div>
        <h2 class="text-2xl font-semibold mb-2">Ingredients</h2>
        <ul>
          <template v-for="(el, ind) of new Array(20)">
            <li v-if="meal[`strIngredient${ind + 1}`]">
              {{ ind + 1 }}. {{ meal[`strIngredient${ind + 1}`] }}
            </li>
          </template>
        </ul>
      </div>
      <div>
        <h2 class="text-2xl font-semibold mb-2">Measures</h2>
        <ul>
          <template v-for="(el, ind) of new Array(20)">
            <li v-if="meal[`strMeasure${ind + 1}`]">
              {{ ind + 1 }}. {{ meal[`strMeasure${ind + 1}`] }}
            </li>
          </template>
        </ul>
      </div>
    </div>
  </div>
</template>
<script setup>
import { onMounted, ref } from "vue";
import axiosClient from "../axiosClient.js";
import { useRoute } from "vue-router";

const route = useRoute();
const meal = ref({});

onMounted(() => {
  axiosClient.get(`/lookup.php?i=${route.params.id}`).then((response) => {
    meal.value = response.data.meals[0] || {};
  });
});
</script>
