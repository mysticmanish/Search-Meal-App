<template>
    <div class="p-8 pb-0">
        <h1>Meals for {{ ingredient.strIngredient }}</h1>
    </div>
    <Meals :meals="meals" />
</template>

<script setup>
import { computed } from '@vue/reactivity';
import { onMounted } from 'vue';
import store from '../store';
import { useRoute } from 'vue-router';
import Meals from '../components/Meals.vue';

const route = useRoute();
const ingredient = computed(() => store.state.ingredient)
const meals = computed(() => store.state.mealsByIngredient)


onMounted(() => {
    store.dispatch('searchMealsByIngredient',route.params.ingredient)
})
</script>

<style scoped>

</style>