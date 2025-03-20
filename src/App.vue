<template>
  <div class="bg-gray-100 h-full">
    <header
      class="bg-white shadow-md h-16 flex justify-between items-stretch px-8"
    >
      <router-link
        v-bind:to="{ name: 'home' }"
        class="inline-flex items-center h-full"
      >
        Home
      </router-link>
      <div>
        <router-link
          to="/"
          class="inline-flex items-center px-2 h-full transition-colors hover:bg-purple-200"
        >
          Search Meals
        </router-link>
        <router-link
          to="/"
          class="inline-flex items-center px-2 h-full transition-colors hover:bg-purple-200"
        >
          Meal by Letter
        </router-link>
        <router-link
          to="/"
          class="inline-flex items-center px-2 h-full transition-colors hover:bg-purple-200"
        >
          Meals by ingredients
        </router-link>
      </div>
    </header>
    <main>
      <router-view> </router-view>
    </main>
  </div>
</template>

<script setup></script>

<style scoped></style>
