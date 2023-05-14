<script setup>
import { ref } from 'vue'

const abelhas = ref([
  {
    id: 1,
    nome: 'Honey Bee',
    quantidade: 0,
    preco: 150
  },
  {
    id: 2,
    nome: 'Bumble Bee',
    quantidade: 0,
    preco: 45.99
  },
  {
    id: 3,
    nome: 'Fuzzy Bee',
    quantidade: 0,
    preco: 350.0
  },
  {
    id: 4,
    nome: 'Bomber Bee',
    quantidade: 0,
    preco: 175.0
  },
  {
    id: 5,
    nome: 'Ninja Bee',
    quantidade: 0,
    preco: 199.0
  },
  {
    id: 6,
    nome: 'Music Bee',
    quantidade: 0,
    preco: 299.99
  },
  {
    id: 7,
    nome: 'Guardian Bee',
    quantidade: 0,
    preco: 249.99
  },
  {
    id: 8,
    nome: 'Rage Bee',
    quantidade: 0,
    preco: 24.99
  },
  {
    id: 9,
    nome: 'Stubborn Bee',
    quantidade: 0,
    preco: 29.99
  },
  {
    id: 10,
    nome: 'Diamond Bee',
    quantidade: 0,
    preco: 189.0
  },
  {
    id: 11,
    nome: 'Demon Bee',
    quantidade: 0,
    preco: 49.99
  },
  {
    id: 12,
    nome: 'Fire Bee',
    quantidade: 0,
    preco: 59.99
  }
])

const cestinha = ref({
  items: [],
  total: 0
})

let valorTotal = ref(0)

function addcestinha(abelha) {
  cestinha.value.items.push({
    id: abelha.id,
    nome: abelha.nome,
    preco: abelha.preco,
    quantidade: abelha.quantidade,
    total: abelha.preco * abelha.quantidade
  });
  cestinha.value.total += abelha.preco * jogo.quantidade
}

function mais(index) {
  abelhas.value[index].quantidade++
  const pos = cestinha.value.items.indexOf(cestinha.value.items.find(c => c.id === abelhas.value[index].id))
  if (pos != -1) {
    cestinha.value.total -= cestinha.value.items[pos].total
    cestinha.value.items[pos].total = ++cestinha.value.items[pos].quantidade * cestinha.value.items[pos].preco
    cestinha.value.total += cestinha.value.items[pos].total

  }
}

function menos(index) {
  abelhas.value[index].quantidade--
  const pos = cestinha.value.items.indexOf(cestinha.value.items.find(c => c.id === abelhas.value[index].id))


  if (pos != +1) {
    cestinha.value.total -= cestinha.value.items[pos].total
    cestinha.value.items[pos].total = --cestinha.value.items[pos].quantidade * cestinha.value.items[pos].preco
    cestinha.value.total += cestinha.value.items[pos].total
  }
}

function clear(){
cestinha.value.items = []
cestinha.value.total = 0
}

</script>

<template>    
    <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
          <div class="modal-header">
            <p class="modal-title fs-5" id="exampleModalLabel">BEES</p>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
          <div class="modal-body">
            <div v-for="(carrinhoItem, index) in cestinha.items" :key="index">              
              <strong> {{ carrinhoItem.id }} - {{ carrinhoItem.nome }}</strong>
              <hr>
              <p>Preço BRL: {{ carrinhoItem.preco }} </p> 
              <p>Quantidade: {{ carrinhoItem.quantidade }} </p>
              <p>Preço: {{ carrinhoItem.total }}</p>
            </div>
            
            <p v-if="cestinha.items.length > 0">Total: {{ cestinha.total }} BRL</p>
            <p v-else>Nenhum Item</p>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
            <button @click="clear" type="button" class="btn btn-warning">Clear</button>
          </div>
        </div>
      </div>
    </div>

  <div class="barra">
    <h1>🐝BEE SHOP🐝</h1>
  </div>
  <div class="container">
    <button type="button" class="btn btn-primary p-3 mt-2 " data-bs-toggle="modal" data-bs-target="#exampleModal">
      🧺 Cestinha
    </button>
    <div class="row">
      <div v-for="(jogo, index) in abelhas" :key="jogo.id" class="tema col-3">
        <h1>{{ jogo.id }} - {{ jogo.nome }}</h1>
        <br />
        <h6>Preço: {{ jogo.preco }} Honey</h6>
        <h6>Quantidade: {{ jogo.quantidade }}</h6>

        <button type="button" @click="menos(index)" class="button">-</button>
        <button type="button" @click="addcestinha(jogo)" class="button">Add</button>
        <button type="button" @click="mais(index)" class="button">+</button>
      </div>
    </div>
  </div>
  <div class="barra">
    <h1>BEE SWARM SIMULATOR</h1>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat&display=swap');

 
/* Estilo da barra superior */
.barra {
background-color: #FCD307;
text-align: center;
padding: 20px 0;
}

/* Estilo do título */
h1 {
color: #8C3F11;
font-weight: bold;
font-size: 30px;
text-shadow: 2px 2px #FCD307;
}

/* Estilo dos botões da lista de compras */
.btn-primary {
background-color: #FCD307;
border-color: #FCD307;
}

.btn-primary:hover {
background-color: #E2B007;
border-color: #E2B007;
}

.btn-primary:focus, .btn-primary.focus {
box-shadow: 0 0 0 0.2rem rgba(252, 211, 7, 0.5);
}

.btn-secondary {
background-color: #FCD307;
border-color: #FCD307;
color: #8C3F11;
}

.btn-secondary:hover {
background-color: #E2B007;
border-color: #E2B007;
color: #8C3F11;
}

.btn-secondary:focus, .btn-secondary.focus {
box-shadow: 0 0 0 0.2rem rgba(252, 211, 7, 0.5);
}

.btn-warning {
background-color: #FCD307;
border-color: #FCD307;
color: #8C3F11;
}

.btn-warning:hover {
background-color: #E2B007;
border-color: #E2B007;
color: #8C3F11;
}

.btn-warning:focus, .btn-warning.focus {
box-shadow: 0 0 0 0.2rem rgba(252, 211, 7, 0.5);
}

/* Estilo do modal */
.modal-header {
background-color: #FCD307;
color: #8C3F11;
border-bottom: 0;
}

.modal-body {
background-color: #F6F6F6;
}

.modal-footer {
background-color: #F6F6F6;
border-top: 0;
}

/* Estilo da lista de compras */
.tema {
background-color: #FFFFFF;
border: 1px solid #EAEAEA;
padding: 20px;
margin-bottom: 20px;
text-align: center;
box-shadow: 2px 2px 10px #EAEAEA;
}

.tema h1 {
font-size: 24px;
font-weight: bold;
margin-bottom: 10px;
color: #8C3F11;
}

.tema h6 {
font-size: 18px;
margin-bottom: 10px;
color: #8C3F11;
}

.button {
background-color: #FCD307;
color: #8C3F11;
border: none;
padding: 10px 20px;
font-size: 20px;
margin: 10px;
cursor: pointer;
transition: background-color 0.2s;
}

.button:hover {
background-color: #E2B007;
}

hr {
border-top: 1px solid
  }

</style>