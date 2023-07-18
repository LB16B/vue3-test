<script setup lang="ts">
import { ref, Ref } from 'vue'
import FoodPostForm from './FoodPostForm.vue';
import FoodList from './FoodList.vue';

export type Food = {
    id: number,
    ingredient: string,
    amount: number,
}

const foods : Ref<Food[]> = ref([{id: 0, ingredient: 'にんじん', amount: 1}, {id: 1, ingredient: 'だいこん', amount: 3}])

const registerFood = (food: Food) => {
    foods.value.push(food)
}

const deleteFood = (id: number) => {
    foods.value = foods.value.filter(f => f.id !== id)
}

</script>

<template>
    <h1>必要な材料</h1>
    <div class="container">
        <FoodPostForm @register="registerFood" />
        <div class="list-container">
            <ul>
                <FoodList :foods="foods" @delete="deleteFood" />
            </ul>
        </div>
    </div>
</template>

<style scoped>

h1 {
    text-align: center;
}

.container {
    display: flex;
    flex-direction: column;
    align-items: center;
}
</style>
