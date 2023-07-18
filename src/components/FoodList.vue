<script setup lang="ts">
import { Food } from './Food.vue'

type Props = {
    foods: Food[]
}

defineProps<Props>()
const emit = defineEmits(['delete'])

const onClickDelete = (id: number, ingredient: string) => {
    if (confirm('Delete' + ingredient + '?')) {
        emit('delete', id)
    }
}
</script>

<template>
    <li v-for="food in foods" :key="food.id" class="food-list">
        <span>{{ food.ingredient }}</span>
        <span>{{ food.amount }}</span>
        <button @click="onClickDelete(food.id, food.ingredient)">delete</button>
    </li>
</template>

<style scoped>
.food-list {
    display: flex;
    justify-content: space-between;
    list-style: none;
    margin-bottom: 8px;
    width: 350px;
    height: 20px;
    align-items: center;
    padding: 10px;
    background: rgb(247, 204, 211);
    border-radius: 8px;
    font-weight: bold;
}
</style>