<script setup>
import WelcomeItem from './WelcomeItem.vue'
import axios from 'axios'
</script>

<template>
  <div>
    <div>
      <button v-on:click="sendPost(cardapios)">Traduzir</button>
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
      let key = '34019a6e-6749-ef74-b468-ab32081bddeb:fx'
      let texto = ''

      cardapio.map((item)=>{
        let texto2= `&text=${item.categoria} ${item.produto} ${item.descricao}.`
        texto = texto + texto2
      })

      console.log(`https://api-free.deepl.com/v2/translate?auth_key=${key}${texto}, world&target_lang=US`)

      axios
      .post(`https://api-free.deepl.com/v2/translate?auth_key=${key}${texto}, world&target_lang=DE`)
      .then(response => console.log(response))
      
      
      // axios.get(
      //   `http://localhost:3000/local/user/3078`
      // ).then(response => console.log(response.data))
      
    }
  }
};
</script>