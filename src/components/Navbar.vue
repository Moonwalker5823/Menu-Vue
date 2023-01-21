<template>
  <header class="bg-white shadow h-16 flex justify-between items-center">
    <router-link
      :to="{ name: 'home' }"
      class="inline-flex items-center h-full px-5 hover:text-blue-300"
    >
      Home
    </router-link>
    <div class="flex items-center gap-1">
      <router-link
        :to="{ name: 'byName' }"
        class="inline-flex item-center h-full px-2  transition-colors hover:text-blue-300"
      >
        Search Meals
      </router-link>
      <router-link
        :to="{ name: 'byLetter' }"
        class="inline-flex item-center px-2 h-full transition-colors hover:text-blue-300"
      >
        Meals By Letter
      </router-link>
      <router-link
        :to="{ name: 'ingredients' }"
        class="inline-flex item-center px-2 h-full transition-colors hover:text-blue-300"
      >
        Meals By Ingredients
      </router-link>
    </div>
  </header>
</template>
