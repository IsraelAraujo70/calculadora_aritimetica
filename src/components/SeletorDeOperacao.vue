<script setup>
    const props = defineProps(['realizarOperacao'])
</script>
<template>
    <div class="operadores">
        <select @change="props.realizarOperacao" class="operador-seletor">
            <option value="somar">Soma</option>
            <option value="subtracao">Subtração</option>
            <option value="multiplicar">Multiplicação</option>
            <option value="dividir">Divisão</option>
            <option value="exponenciacao">Exponenciação</option>
            <option value="raiz">Raiz</option>
        </select>
    </div>
</template>
<style scoped>
.operadores{
    margin-top: 3em;
}

.operador-seletor {
    width: 200px;
    padding: 10px;
    border: none;
    border-radius: 10px;
    font-size: 1rem;
    color: #ffffff;
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.3);
    background: linear-gradient(#1f1f2e, #1f1f2e) padding-box, 
                linear-gradient(45deg, #ff0000, #ff9900, #ff00ff) border-box; 
    border: 3px solid transparent; 
    background-color: #1f1f2e;
    outline: none;
}
</style>