<script setup>
import WelcomeItem from './WelcomeItem.vue'
import axios from 'axios'
</script>

<template>
  <div>
    <div>
      <button v-on:click="sendPost(cardapio)">Traduzir</button>
    </div>
    <div v-for="cardapio in cardapios" :key="cardapio.categoria">
      <p>{{cardapio.categoria}}</p>
    </div>
    <div v-for="cardapio in cardapios" :key="cardapio.produto">
      <h1>{{ cardapio.produto }}</h1>
      <p>{{ cardapio.descricao }}</p>
    </div>
  </div>
</template>

<script>
function saveText(text, filename){
    var a = document.createElement('a');
    a.setAttribute('href', 'data:text/plain;charset=utf-8,'+encodeURIComponent(text));
    a.setAttribute('download', filename);
    a.click()
    }

export default {
  data() {
    return {
      cardapios: [
        {
          produto: 'X-burguer',
          categoria:'Lanche',
          descricao: 'Pão com hamburguer, queijo, alface e tomate'
        },
        {
          produto: 'Coxinha de frango',
          categoria: 'Salgado',
          descricao: 'Massa crocante feita com batata e recheiro de frango caipira temperado, com queijo gorgonzola'
        },
        {
          produto: 'Água',
          categoria: 'Bebida',
          descricao: 'Garrafa 500ml'
        }
      ]
    };
  },
  methods: {

    sendPost(cardapio) {
      let key = '8226e86d-c253-0bea-94a1-d12e4e3b828c:fx'
      axios.post(
        `https://api-free.deepl.com/v2/translate?auth_key=${key}&text=Hello, world&target_lang=DE`
        ).then(response => console.log(response))
      // axios.get(
      //   `http://localhost:3000/local/user/3078`
      // ).then(response => console.log(response.data))
      
    }
  }
};
</script>