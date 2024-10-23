<script setup>
    const props = defineProps(['resultado'])
</script>
<template>
    <div class="resultado mt-5">
        <p>{{ props.resultado }}</p>
    </div>
</template>
<style scoped>
.resultado{
    width: 150px;
    margin: 0 auto;
    background: linear-gradient(#07070f, #07070f) padding-box, 
                linear-gradient(45deg, #ff0000, #ff9900, #ff00ff) border-box; 
    border: 3px solid transparent; 
    border-radius: 5px;
}
.resultado p {
    margin-top: 1rem;
}
</style>