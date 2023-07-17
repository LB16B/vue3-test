<script setup lang="ts">
import { ref } from 'vue'
const foods = ref([{ id: 0, ingredient: 'にんじん'}, { id: 1, ingredient: 'だいこん'}])
const inputtingIngredient = ref<string>('')

const postFood = () => {
    const food = { id: Math.random(), ingredient: inputtingIngredient.value }
    foods.value.push(food)
    inputtingIngredient.value = ''
    console.log('inputting', inputtingIngredient.value)
}

const deleteFood = (id: number) => {
    foods.value = foods.value.filter(f => f.id !== id)
}
</script>

<template>
    <h1>Food</h1>
    <div class="container">
        <div class="form-container">
            <input v-model="inputtingIngredient" />
            <button class="save-button" @click="postFood()">追加する</button>
        </div>
        <p v-if="foods.length <= 0" class="error">何も登録されていません</p>
        <div class="food-container">
            <ul>
                <li v-for="food in foods" :key="food.id" class="food-list">
                    <span>{{ food.ingredient }}</span>
                    <button @click="deleteFood(food.id)" class="delete-button">削除する</button>
                </li>
            </ul>
        </div>
    </div>
</template>

<style scoped>
h1 {
    text-align: center;
}

input {
    margin: 40px auto;
    width: 300px;
    text-align: center;
}

.error {
    text-align: center;
    color: red;
}

.food-list {
    display: flex;
    padding: 15px 100px;
    justify-content: space-between;
}

.save-button {
    width: 100px;
    margin: 10px auto;
}
.delete-button {
    width: 100px;
}

.form-container {
    background: aliceblue;
    width: 700px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
}

.food-container {
    width: 700px;
    margin: 0 auto;
    text-align: center;
}



li {
    list-style: none;
    background: rgb(241, 214, 234);
    margin-bottom: 8px;
}
</style>
