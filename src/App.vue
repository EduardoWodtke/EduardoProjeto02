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

let listaDeCompras = ref([])

function adicionar (){
    produtos.value.push(listaDeCompras.value)

  }
</script>

<template>
  <div class="produtos-container">
    <div v-for="item in produtos" :key="item.id">
      <p>{{ item.nome }}</p>
      <p id="preco">{{ item.preco }}</p>
      <button @click="adicionar">Adicionar</button>
    </div>
  </div>
</template>

<style scoped>
/* * {
  margin: 0%;
  padding: 0%;
} */

.produtos-container {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  grid-template-rows: repeat(4, auto);
  grid-gap: 20px;
}

p {
  font-weight: bolder;
  font-size: 18px;
  border-bottom: 2px solid black;
  padding-bottom: 0px;
  margin: 10px;
}

#preco{
  font-weight: normal;
  border-bottom: none;
}
</style>