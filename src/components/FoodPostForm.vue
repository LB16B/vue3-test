<script setup lang="ts">
import { ref, computed } from 'vue';
const inputtingIngredient = ref<string>('')
const inputtingAmount = ref<number>(0)

const emit = defineEmits(['register'])

const register = () => {
    const food = { id: Math.random(), ingredient: inputtingIngredient.value, amount: inputtingAmount.value }
    console.log(food)
    emit('register', food)
}

const ingredientLengthLimit = 15

const isValidIngredient = computed(() => {
    if (inputtingIngredient.value.length >= ingredientLengthLimit) {
        return false
    } else {
        return true
    }
})

const color = computed(() => {
    return isValidIngredient.value ? 'white' : 'red'
})

</script>

<template>
    <div class="form-container">
        <div class="input-container">
            <div>
                <span>ingredient:</span>
                <input class="input-ingredient" v-model="inputtingIngredient" />
            </div>
            <div>
                <span>amount:</span>
                <input class="input" v-model="inputtingAmount" type="number" />
            </div>
        </div>
        <span class="error-message" v-if="!isValidIngredient">{{ ingredientLengthLimit }} characters or less, please</span>
        <button :disabled="!isValidIngredient" @click="register" class="register-button">register</button>
    </div>
</template>

<style scoped>


.form-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    background: rgb(255, 248, 227);
    width: 700px;
    padding: 20px;
    text-align: center;
}

.input-container {
    display: flex;
    justify-content: space-between;
    height: 50px;
    margin: 20px 0;
}

.input {
    margin-bottom: 10px;
    width: 200px;
    margin-right: 20px;
}
.input-ingredient {
    background: v-bind(color);
    margin-bottom: 10px;
    width: 200px;
    margin-right: 20px;
}

span {
    font-weight: bold;
    font-size: 1.2rem;
    margin-right: 5px;
}

.register-button {
    width: 80px;
    height: 35px;
    background: rgb(173, 235, 173);
    border-radius: 8px;
    border: 1px solid rgb(173, 235, 173);
}

.register-button:hover {
    opacity: .8;
}

.error-message {
    color: red;
}
</style>