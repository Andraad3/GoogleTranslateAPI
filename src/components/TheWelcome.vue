<script setup>
import WelcomeItem from './WelcomeItem.vue'
import { traduz } from '../post.mjs'
</script>

<template>
  <div>
    <div>
      <button v-on:click="sendPost('Batata')">Traduzir</button>
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

    sendPost(palavras) {
      let obj = {
        q: palavras,
        target: "us",
      }
      saveText( JSON.stringify(obj), "request.json" );
      const valorTraduzido =  traduz()
      console.log('traducao: ', valorTraduzido)
    }
  }
};
</script>