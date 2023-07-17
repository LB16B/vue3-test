<script setup lang="ts">
import { defineProps } from 'vue';
type Food = {
    id: number,
    ingredient: string
}

type Props = {
    foods: Food[]
}

const deleteFood = (id: number) => {
    console.log('delete')
}

defineProps<Props>()
</script>

<template>
    <li v-for="food in foods" :key="food.id" class="food-list">
        <span>{{ food.ingredient }}</span>
        <button @click="deleteFood(food.id)" class="delete-button">削除する</button>
    </li>
</template>

<style scoped>
.food-list {
    display: flex;
    padding: 15px 100px;
    justify-content: space-between;
}

.delete-button {
    width: 100px;
}

li {
    list-style: none;
    background: rgb(241, 214, 234);
    margin-bottom: 8px;
}
</style>