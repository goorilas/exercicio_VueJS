<script setup>
import { reactive } from 'vue';

const estado = reactive({
    numeroUm: 0,
    numeroDois: 0,
    filtro: 'selecionar',
    resultado: 0
})

const calcular = () => {
    switch (estado.filtro) {
        case 'soma':
            estado.resultado = estado.numeroUm + estado.numeroDois;
            return estado.resultado
        case 'subtracao':
            estado.resultado = estado.numeroUm - estado.numeroDois;
            return estado.resultado
        case 'multiplicacao':
            estado.resultado = estado.numeroUm * estado.numeroDois;
            return estado.resultado
        case 'divisao':
            estado.resultado = estado.numeroDois !== 0 ? estado.numeroUm / estado.numeroDois : 'Não pode ser (0).';
            return estado.resultado
    }
}
</script>

<template>
    <div class="container text-center border mt-2">
        <h1 class="text-center">Calculadora Aritmética</h1>
        <div class="row">
            <div class="col-12 p-2">
                <input v-model.number="estado.numeroUm" type="number" placeholder="Número a ser calculado" />
            </div>
            <div class="col-12 p-2">
                <input v-model.number="estado.numeroDois" type="number" placeholder="Número a ser calculado" />
            </div>
            <div class="col-12 d-flex justify-content-center p-2">
                <select v-model="estado.filtro" @change="calcular" class="form-control text-center w-50">
                    <option value="selecionar">Selecione uma operação</option>
                    <option value="soma">Soma (+)</option>
                    <option value="subtracao">Subtração (-)</option>
                    <option value="multiplicacao">Multiplicação (x)</option>
                    <option value="divisao">Divisão (÷)</option>
                </select>
            </div>
            <h4>Resultado</h4>
            <div class="col-12 p-2">
                <h2>Resultado: {{ estado.resultado }}</h2>
            </div>
        </div>
    </div>
</template>

<style scoped>
.border {
    border-radius: 30px;
    width: 30%;
    box-shadow: 5px 5px 5px rgb(24, 33, 116);
    border-color: 3px solid rgb(74, 31, 122);
    background-image: radial-gradient(rgba(123, 123, 207, 0.685), rgba(131, 54, 231, 0.596), rgb(110, 110, 172));
}
</style>