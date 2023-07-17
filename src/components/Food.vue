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

</script>

<template>
    <h1>Food</h1>
    <div class="container">
        <div class="form-container">
            <input v-model="inputtingIngredient" />
            <button class="save-button" @click="postFood()">追加する</button>
        </div>
        <div class="food-container">
            <ul>
                <li v-for="food in foods" :key="food.id">
                    <span>{{ food.ingredient }}</span>
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

.save-button {
    width: 100px;
    margin: 10px auto;
}
.container {

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
