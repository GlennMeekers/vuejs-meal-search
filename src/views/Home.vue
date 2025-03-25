<template>
  <div class="flex flex-col p-8">
    <div class="flex justify-center gap-2 mt-2">
      <router-link
        v-bind:to="{ name: 'byLetter', params: { letter } }"
        v-bind:key="letter"
        v-for="letter in letters"
      >
        {{ letter }}
      </router-link>
    </div>

    <pre>{{ ingredients }}</pre>
  </div>
</template>

<script setup>
import { computed, onMounted, ref } from "vue";
import store from "../store/index.js";
import axiosClient from "../axiosClient.js";

const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ".split("");
const ingredients = ref([]);

onMounted(() => {
  axiosClient.get("/list.php?i=list").then((reponse) => {
    console.log(reponse.data);
    ingredients.value = reponse.data.meals;
  });
});
</script>
