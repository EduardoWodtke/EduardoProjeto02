<script setup>
import { ref } from 'vue'

const produtos = ref([
{
id: 1,
nome: 'Camiseta',
preco: 49.9
},
{
id: 2,
nome: 'Calça',
preco: 99.9
},
{
id: 3,
nome: 'Meia',
preco: 9.9
},
{
id: 4,
nome: 'Sapato',
preco: 199.9
},
{
id: 5,
nome: 'Boné',
preco: 29.9
},
{
id: 6,
nome: 'Óculos',
preco: 99.9
},
{
id: 7,
nome: 'Relógio',
preco: 299.9
},
{
id: 8,
nome: 'Bermuda',
preco: 79.9
},
{
id: 9,
nome: 'Cueca',
preco: 19.9
},
{
id: 10,
nome: 'Meia',
preco: 9.9
}
])
</script>

<template>
<div v-for="item in produtos" :key="item.id" id="container">
<p >{{ item.nome }}</p>
<p>{{ item.preco }}</p>
</div>
</template>

<style scoped>
*{
margin: 0%;
padding: 0%;
}

p {
font-weight: bolder;
font-size: 18px;
border-bottom: 2px solid black;
padding: 10px;
}
</style>

