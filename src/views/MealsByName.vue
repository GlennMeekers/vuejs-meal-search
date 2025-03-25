<template>
  <div class="p-8 pb-0">
    <input
      type="text"
      v-model="keyword"
      class="rounded border-2 border-gray-200 w-full"
      placeholder="Search for Meals"
      @change="searchMeals"
    />
  </div>

  <div class="grid grid-cols-1 md:grid-cols-3 gap-5 p-8">
    <div
      v-for="meal in meals"
      v-bind:key="meal.idMeal"
      class="bg-white rounded-xl shadow"
    >
      <router-link :to="{ name: 'mealDetails', params: { id: meal.idMeal } }">
        <img
          class="rounded-t-xl w-full h-48 object-cover"
          :src="meal.strMealThumb"
          :alt="meal.strMeal"
        />
      </router-link>
      <div class="p-3">
        <h3 class="my-3 font-semibold">{{ meal.strMeal }}</h3>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Ad eligendi
          ex commodi blanditiis nesciunt ullam officia praesentium accusantium
          libero magni.
        </p>
        <a
          class="my-3 px-3 py-2 rounded inline-block border-2 border-red-500 bg-red-500 hover:bg-red-600 text-white transition"
          :href="meal.strYoutube"
          target="_blank"
          >YouTube</a
        >
      </div>
    </div>
  </div>
</template>
<script setup>
import { computed } from "@vue/reactivity";
import { onMounted, ref } from "vue";
import { useRoute } from "vue-router";
import store from "../store/index.js";

const route = useRoute();
const keyword = ref("");
const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
  store.dispatch("searchMeals", keyword.value);
}

onMounted(() => {
  keyword.value = route.params.name;

  if (keyword.value) {
    searchMeals();
  }
});
</script>
