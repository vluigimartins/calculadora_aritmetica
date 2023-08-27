<script setup>
import { reactive } from 'vue';

const estado = reactive({
    numero1: 0,
    numero2: 0,
    operacao: '+',
})

const getAdicao = () => estado.numero1 + estado.numero2;
const getSubtracao = () => estado.numero1 - estado.numero2;
const getMultiplicacao = () => estado.numero1 * estado.numero2;
const getDivisao = () => estado.numero1 / estado.numero2;

const getOperacao = () => {
    switch (estado.operacao) {
        case '+':
            return getAdicao();
        case '-':
            return getSubtracao();
        case '*':
            return getMultiplicacao();
        case '/':
            return getDivisao();
        default:
            return 0;
    }
}
</script>

<template>
    <div class="container bg-light">
        <header class="p-5 mb-5 mt-5 bg-secondary bg-gradient text-center">
            <h1>Calculadora Aritmética</h1>
        </header>
        <form>
            <div class="row">
                <div class="col">
                    <input class="form-control border-secondary" v-model="estado.numero1" type="number" @input="getOperacao" />
                </div>
                <div class="col text-center">
                    <select class="select" v-model="estado.operacao" @change="getOperacao">
                        <option value="+">+</option>
                        <option value="-">-</option>
                        <option value="*">*</option>
                        <option value="/">/</option>
                    </select>
                </div>
                <div class="col">
                    <input class="form-control border-secondary" v-model="estado.numero2" type="number" @input="getOperacao" />
                </div>
            </div>
            <div class="row mt-5 text-center">
                <h2>Resultado = {{ getOperacao() }}</h2>
            </div>
        </form>
    </div>
</template>

<style scoped>
.select {
    width: 80px;
}
</style>
