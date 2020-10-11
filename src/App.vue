<template>
  <div id="app">
    <Nav></Nav>
    <v-app>
      <v-container>
        <v-layout row wrap>
          <v-flex md12 lg12 xs12 pl-5 pr-5>
            <v-text-field
              label="O que você deseja buscar?"
              type="text"
              v-model="search"
              clearable
              dark
              :append-outer-icon="'mdi-send'"
              @click:append-outer="fetchGifs"
            >
            </v-text-field>
          </v-flex>
          <v-flex
            md4 lg4 xs4 pb-8
            v-for="gif in gifs"
            v-bind:key="gif.images.original.url">
            <Grid
              :show="false"
              :src="gif.images.original.url"
              :titulo="gif.username"
              :descricao="gif.slug"
            >
            </Grid>
          </v-flex>
        </v-layout>
      </v-container>
    </v-app>
    <Footer></Footer>
  </div>
</template>

<script>
import Nav from "./components/Nav";
import Footer from "./components/Footer";
import Grid from "./components/Grid";

export default {
  name: "App",
  components: {
    Nav,
    Footer,
    Grid,
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
      return this.gifs.filter(function (gif) {
        return gif.index < 4;
      });
    },
  },
  methods: {
    fetchGifs: function () {
      var url = "";
      if (this.search) {
        console.log(this.search);
        url = `${this.apiUrl}search?q=${this.search}&rating=g&api_key=${this.apiKey}`;
      } else {
        console.log();
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