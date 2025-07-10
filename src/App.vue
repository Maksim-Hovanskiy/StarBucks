<script setup>
import Cooking from "./components/cooking.vue";
import Success from "./components/Success.vue";
import TheHeader from "./components/TheHeader.vue";
import TheHero from "./components/TheHero.vue";
</script>

<template>
  <TheHeader />
  <main>
    <TheHero />
    <Success />
    <Cooking />
  </main>
</template>

<style scoped></style>
