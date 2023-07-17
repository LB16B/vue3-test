<script setup lang="ts">
import { ref, defineEmits } from 'vue'
const inputtingIngredient = ref<string>('')

const emit = defineEmits(['post-food'])
const postFood = () => {
    emit('post-food', inputtingIngredient.value)
    inputtingIngredient.value = ''
}

</script>

<template>
    <div class="form-container">
        <input v-model="inputtingIngredient" />
        <button class="save-button" @click="postFood">追加する</button>
    </div>
</template>

<style scoped>

input {
    margin: 40px auto;
    width: 300px;
    text-align: center;
}

.form-container {
    background: aliceblue;
    width: 700px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
}

.save-button {
    width: 100px;
    margin: 10px auto;
    
}

</style>