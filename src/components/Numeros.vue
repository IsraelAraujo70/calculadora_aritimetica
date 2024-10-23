<script setup>
    const props = defineProps(['primeiroNumero', 'segundoNumero', 'operadores'])
</script>
<template>
    <h2>Insira os números:</h2>
        <div class="numeros">
            <input type="number" @keyup="props.primeiroNumero" @change="props.operadores">
            <input type="number" @keyup="props.segundoNumero" @change="props.operadores">
        </div>
</template>
<style scoped>
.numeros {
    display: flex;
    gap: 15px;
    justify-content: center;
    margin-top: 20px;
}

.numeros input {
    width: 100px;
    padding: 10px;
    border: none; 
    border-radius: 5px; 
    font-size: 1rem;
    background: linear-gradient(#ffffff, #ffffff) padding-box, 
                linear-gradient(45deg, #ff0000, #ff9900, #ff00ff) border-box; 
    border: 3px solid transparent; 
    color: #07070f;
}
</style>