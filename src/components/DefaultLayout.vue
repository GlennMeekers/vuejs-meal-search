<template>
  <div class="bg-gray-100">
    <Navbar />
    <main>
      <router-view></router-view>
    </main>
  </div>
</template>

<script setup>
import Navbar from "./Navbar.vue";
</script>
