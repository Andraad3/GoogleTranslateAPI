<script setup>
import WelcomeItem from "./WelcomeItem.vue";
import axios from "axios";
</script>

<template>
  <div>
    <div>
      <button v-on:click="sendPost(cardapios)">Traduzir</button>
    </div>
    <div v-for="cardapio in cardapios" :key="cardapio.categoria">
      <p>{{ cardapio.categoria }}</p>
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
        // {
        //   produto: 'X-burguer',
        //   categoria:'Lanche',
        //   descricao: 'Pão com hamburguer, queijo, alface e tomate'
        // },
        // {
        //   produto: 'Coxinha de frango',
        //   categoria: 'Salgado',
        //   descricao: 'Massa crocante feita com batata e recheiro de frango caipira temperado, com queijo gorgonzola'
        // },
        // {
        //   produto: 'Água',
        //   categoria: 'Bebida',
        //   descricao: 'Garrafa 500ml'
        // }
        {
          produto: "Original",
          descricao: "Original GF - 600ml",
        },
        {
          produto: "Brahma",
          descricao: "Brahma GF - 600ml",
        },
        {
          produto: "Serramalte",
          descricao: "Serramalte GF- 600ml",
        },
        {
          produto: "Colorado Appia",
          descricao: "Colorado Appia GF - 600ml",
        },
        {
          produto: "Corona",
          descricao: "Corona GF - long neck",
        },
        {
          produto: "Brahma  Zero",
          descricao: "Brahma Zero - 355ml",
        },
        {
          produto: "Franziskaner Hell",
          descricao: "Franziskaner Hefe GF - 500ml",
        },

        {
          produto: "Hoegaarden ",
          descricao: "Hoegaarden GF -long neck",
        },
        {
          produto: "Beck's Pilsner",
          descricao: "Beck's Pilsner GF- long neck",
        },
        {
          produto: "Wälls Session",
          descricao: "600 ML",
        },
        {
          produto: "Budweiser ",
          descricao: "Budweiser GF- 550ml",
        },
        { produto: "Budweiser", descricao: "Budweiser GF- long neck" },
        { produto: "Stella Artois ", descricao: "Stella Arotis GF- 550ml" },
        { produto: "Stella Artois ", descricao: "Stella Artois GF- long neck" },
        {
          produto: "Colorado Ribeirão",
          descricao: "Colorado Ribeirão GF- 600ml",
        },
        { produto: "Colorado Indica", descricao: "Colorado Indica GF- 600ml" },
        {
          produto: "Colorado Demoiselle",
          descricao: "Colorado Demoiselle GF- 600ml",
        },
        { produto: "Chopp ", descricao: "" },
        { produto: "Wälls Hop com", descricao: "600ML" },
        { produto: "Wälls Witte", descricao: "600ML" },
        { produto: "Wälls Pilsner", descricao: "600ML" },
        { produto: "Brahma Extra Weiss", descricao: "355ML" },
        { produto: "Patagonia Amber", descricao: "740ML" },
        { produto: "Patagonia Weisse", descricao: "740ML" },
        { produto: "Patagonia Bohemian", descricao: "740ML" },
        { produto: "Leffe Blonde", descricao: "" },
        { produto: "Stella Artois", descricao: "" },
        { produto: "Malzebier", descricao: "" },
        { produto: "Spaten", descricao: "" },
        { produto: "Beck´s", descricao: "" },
        { produto: "Brahma duplo malte", descricao: "" },
        { produto: "Boehmia Puro Malte", descricao: "" },
        { produto: "Spaten", descricao: "" },
        { produto: "Michelob Ultra", descricao: "" },
        { produto: "Goose Island Midway", descricao: "" },
        {
          produto: "Flavor & Tonic",
          descricao:
            "Absolut flavor mango, triple sec, água tônica e fatias de morango.",
        },
        {
          produto: "Tardezinha",
          descricao:
            "Absolut, suco de laranja, suco de grapefruit, suco de limão siciliano, xarope de framboesa e água com gás.",
        },
        {
          produto: "Grapefruit Julep",
          descricao: "Absolut, grapefruit, limão, mel e hortelã.",
        },
        {
          produto: "Extrakt PGS",
          descricao:
            "Absolut Extrakt, suco de cranberry, limão e xarope de gengibre.",
        },
        {
          produto: "Balla Honey Passion",
          descricao: "Ballantine's Finest, maracujá, limão siciliano e mel.",
        },
        {
          produto: "Irish Sour",
          descricao:
            "Jameson Whiskey, suco de limão, xarope de amêndoas e hortelã.",
        },
        {
          produto: "Vanilla Drop",
          descricao: "Absolut Vanilla, limão e triple sec.",
        },
        { produto: "Jack & Coke", descricao: "Jack Daniel's e Pepsi." },
        {
          produto: "Gentleman Sour",
          descricao:
            "Gentleman Jack, suco de limão taiti, xarope de açúcar, laranja e cereja.",
        },
        {
          produto: "Jack Honey Lemonade",
          descricao: "Jack Daniel's Honey, suco de limão siciliano e soda.",
        },
        {
          produto: "Maracujack",
          descricao:
            "Jack Daniel's, polpa de maracujá, xarope de açúcar, suco de limão e soda.",
        },
        {
          produto: "Cosmopolitan",
          descricao:
            "Absolut, Grand Marnier, suco de limão e suco de cranberry.",
        },
        {
          produto: "Negroni do Didi",
          descricao: "Gin Beefeater, Carpano Punt e MES e Campari",
        },
        {
          produto: "1800 Tonic",
          descricao: "1800 Tequila Silver ( 100% agave) e água tônica.",
        },
        {
          produto: "Canarinho",
          descricao: "Gin Beefeater, Orange Bitters e frutas.",
        },
        {
          produto: "Bramble Foam",
          descricao:
            "Gin Beefeater, suco de limão, xarope de açúcar e espuma de gengibre.",
        },
        {
          produto: "Carajillo 43",
          descricao: "Licor 43 e café expresso.",
        },
        {
          produto: "Manhattan",
          descricao: "Jack Daniel's, Vermute tinto e bitters aromáticos.",
        },
        {
          produto: "Gincaju",
          descricao: "Gin Beefeater, água tônica, caju e limão siciliano.",
        },
        {
          pedido: "Cuervo Margarita",
          descricao:
            "Tequila Jose Cuervo Especial Gold, triple-sec e suco de limão. ",
        },
        {
          pedido: "Cuervo Sunrise",
          descricao:
            "Tequila Jose Cuervo Especial Gold, suco de laranja e grenadine.",
        },
        {
          pedido: "Cuervo Muletta",
          descricao:
            "Tequila Jose Cuervo Especial Silver, limão, açúcar e espuma de gengibre.",
        },
        {
          pedido: "Pisco Sour Capel",
          descricao:
            "Pisco Capel, suco de limão, açúcar, clara de ovo e bitters aromáticos.",
        },
        {
          pedido: "Mojito Clássico",
          descricao:
            "Rum Havana Club 3 anos, suco de limão, xarope de açúcar, hortelã e água com gás.",
        },
        {
          pedido: "Mojito Spiced",
          descricao:
            "Rum Havana club 3 anos, hortelá, limão, laranja, xarope de canela e club soda.",
        },
        {
          pedido: "Moscow Mule",
          descricao:
            "Absolut, Jameson ou Beefeater, limão, açúcar e espuma de gengibre.",
        },
      ],
    };
  },
  methods: {
    sendPost(cardapio) {
      let key = "34019a6e-6749-ef74-b468-ab32081bddeb:fx";
      let textoCategoria = "";
      let textoProduto = "";
      let textoDescricao = "";

      cardapio.map((item) => {
        let textoCategoria2 = `&text=${item.categoria}`;
        let textoProduto2 = `&text=${item.produto}`;
        let textoDescricao2 = `&text=${item.descricao}`;
        textoCategoria = textoCategoria + textoCategoria2;
        textoProduto = textoProduto + textoProduto2;
        textoDescricao = textoDescricao + textoDescricao2;
      });

      axios
        .post(
          `https://api-free.deepl.com/v2/translate?auth_key=${key}${textoDescricao}${textoProduto}&source_lang=PT&target_lang=EN`
          // `https://api-free.deepl.com/v2/translate?auth_key=${key}${textoCategoria}${textoDescricao}${textoProduto}&source_lang=PT&target_lang=EN`
        )
        .then((response) => console.log(response));
    },
  },
};
</script>