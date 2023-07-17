<script setup lang="ts">
import { ref } from 'vue'
import FoodPostForm from './FoodPostForm.vue';
import FoodList from './FoodList.vue';
const foods = ref([{ id: 0, ingredient: 'にんじん'}, { id: 1, ingredient: 'だいこん'}])
// const inputtingIngredient = ref<string>('')

const postFood = (ingredient: string) => {
    const food = { id: Math.random(), ingredient }
    foods.value.push(food)
    // inputtingIngredient.value = ''
}

const deleteFood = (id: number) => {
    foods.value = foods.value.filter(f => f.id !== id)
}
</script>

<template>
    <h1>Food</h1>
    <div class="container">
        <FoodPostForm @post-food="postFood" />
        <p v-if="foods.length <= 0" class="error">何も登録されていません</p>
        <div class="food-container">
            <ul>
                <FoodList :foods="foods" @delete-food="deleteFood" />
            </ul>
        </div>
    </div>
</template>

<style scoped>
h1 {
    text-align: center;
}


.error {
    text-align: center;
    color: red;
}

.food-container {
    width: 700px;
    margin: 0 auto;
    text-align: center;
}

</style>
