<template>
    <div class="container">
        <h1>Calculadora Aritmética</h1>
        <div class="input-group">
        <input v-model.number="numero1" type="number" placeholder="Número 1" />
        <select v-model="operacao">
            <option value="+">Soma (+)</option>
            <option value="-">Subtração (-)</option>
            <option value="*">Multiplicação (*)</option>
            <option value="/">Divisão (/)</option>
        </select>
        <input v-model.number="numero2" type="number" placeholder="Número 2" />
        </div>
        <p class="resultado">Resultado: <strong>{{ resultado }}</strong></p>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const numero1 = ref(0)
const numero2 = ref(0)
const operacao = ref('+')

const resultado = computed(() => {
    switch (operacao.value) {
        case '+': return numero1.value + numero2.value
        case '-': return numero1.value - numero2.value
        case '*': return numero1.value * numero2.value
        case '/': return numero2.value !== 0 ? numero1.value / numero2.value : 'Erro: divisão por zero'
        default: return 0
    }
})
</script>

<style scoped>
    .container {
    max-width: 500px;
    margin: auto;
    padding: 2rem;
    text-align: center;
    }
    .input-group {
    display: flex;
    gap: 1rem;
    justify-content: center;
    margin: 1rem 0;
    }
    input, select {
    padding: 0.5rem;
    font-size: 1rem;
    width: 100px;
    }
    .resultado {
    font-size: 1.2rem;
    color: #333;
    }
</style>
