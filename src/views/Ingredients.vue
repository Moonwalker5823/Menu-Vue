<template>
  <div class="p-8">
    <h1 class="text-4xl font-bold mb-4">Ingredients</h1>
    <input
      type="text"
      v-model="keyword"
      class="rounded border-2 bg-white border-grey-200 w-full mb-3"
      placeholder="Search for Ingredients"
    />
    <router-link
      :to="{
        name: 'byIngredient',
        params: { ingredient: ing.strIngredient },
      }"
      v-for="ing of computedIngredients"
      :key="ing.idIngredient"
      class="block bg-white rounded p-3 mb-3 shadow"
    >
      <h3 class="text-2xl font-bold mb-2">{{ ing.strIngredient }}</h3>
      <p>{{ ing.strDescription }}</p>
    </router-link>
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue";
import { useRoute } from "vue-router";
import { computed } from "@vue/reactivity";
import axiosClient from "../axiosClient.js";
import store from "../store";
import MealItem from "../components/MealItem.vue";

const keyword = ref("");
const ingredients = ref([]);
const computedIngredients = computed(() => {
  if (!computedIngredients) return ingredients;
  return ingredients.value.filter(
    (i) =>
      i.strDescription?.toLowerCase().includes(keyword.value.toLowerCase()) ||
      i.strIngredient.toLowerCase().includes(keyword.value.toLowerCase())
  );
});

onMounted(() => {
  axiosClient.get("list.php?i=list").then(({ data }) => {
    ingredients.value = data.meals;
  });
});
</script>

<style scoped></style>
