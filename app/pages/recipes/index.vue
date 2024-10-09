<script setup lang="ts">
import { type RecipeResponse } from '~~/types/types';
const { data, error } = await useFetch<RecipeResponse>("https://dummyjson.com/recipes")

useSeoMeta({
    title: "NuxtRecipes - Recipes",
    description: "Recipes for you to cook!",
    ogTitle: "NuxtRecipes",
    ogDescription: "Recipes for you to cook!",
    ogImage: "/nuxt-course-hero.png",
    ogUrl: `http:localhost:3000`,
    twitterTitle: "NuxtRecipes",
    twitterDescription: "Recipes for you to cook!",
    twitterImage: "nuxt-course-hero.png",
    twitterCard: "summary",
});
</script>
<template>
    <div>
        <section class="py-10 container text-center">
            <h2 class="text-3xl lg:text-5xl mb-2">Discover, Create, Share</h2>
            <p class="text-lg lg:text-xl mb-8">Check out our most popular recipes!</p>
            <div v-if="!error" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-x-4 gap-y-8">
                <RecipeCard v-for="recipe in data?.recipes" :recipe="recipe" />
            </div>
            <p v-else class="text-xl">Opps, something went wrong. Please try again later</p>
        </section>
    </div>
</template>
