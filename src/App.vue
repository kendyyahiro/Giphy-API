<template>
  <div id="app">
    <Nav titulo="Giphy API"></Nav>
    <v-app>
      <v-container>
        <v-layout row wrap>
          <Busca></Busca>
          <v-flex md11 lg11 xs10 class="espacamento-melhorado">
          <v-text-field
            label="Divirta-se!"
            v-model="search"
            placeholder="Divirta-se"
            hide-details="auto"
          >
          </v-text-field>
          </v-flex>
            <v-btn v-on:click="fetchGifs" elevation="2"> OK </v-btn>
          <div v-for="gif in gifs" v-bind:key="gif" class="organiza-gifs-search">
              <Grid :show="false" :src="gif.images.original.url" :titulo="gif.username" :descricao="gif.slug">
              </Grid>
              <!-- <img class="tamanho-padrao-img" :src="gif.images.original.url" alt="" /> -->
          </div>
        <br />
        </v-layout>
      </v-container>

    </v-app>
    <Footer></Footer>
  </div>
</template>

<script>
import Nav from "./components/Nav";
import Busca from "./components/Busca";
import Footer from "./components/Footer";
import Grid from "./components/Grid";

export default {
  name: "App",
  components: {
    Nav,
    Busca,
    Footer,
    Grid
  },
  data() {
    return {
      search: " ",
      apiUrl: "http://api.giphy.com/v1/gifs/",
      apiKey: "iFH6GlogTVgIBunIN0Om1KtBqKITlPZu",
      gifs: null,
    };
  },
  computed: {
    eventGifs: () => {
      return this.gifs.filter(function(gif){
        return gif.index < 4
      })
    }
  },
  methods: {
    fetchGifs: function () {
      var url = "";
      if (this.search) {
        console.log(this.search)
        url = `${this.apiUrl}search?q=${this.search}&rating=g&api_key=${this.apiKey}`;
      } else {
        console.log()
        url = `${this.apiUrl}trending?api_key=${this.apiKey}`;
      }

      fetch(url)
        .then((response) => response.json())
        .then((data) => {
          this.gifs = data.data;
        });
    },

    created: function () {
      this.fetchGifs();
    },

    // pesquisa: function() {
    //   var userInput = this.search;
    //   console.log(userInput);

    //   var giphyAPIKey = "iFH6GlogTVgIBunIN0Om1KtBqKITlPZu"
    //   var giphyAPIUrl = `http://api.giphy.com/v1/gifs/search?q=${userInput}&rating=g&api_key=${giphyAPIKey}`

    //   fetch(giphyAPIUrl).then(function (data) {
    //     return data.json()
    //   })
    //   .then(function (json) {
    //     console.log(json.data[0].images.fixed_height.url)
    //     var imgPath = json.data[0].images.fixed_height.url
    //     var img = document.createElement('img')
    //     img.setAttribute("src", imgPath)
    //     document.getElementById('trazer-gifs').appendChild(img)
    //   })

    // }
  },
};
</script>

<style>

</style>