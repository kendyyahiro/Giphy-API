<template>
  <div id="app">
    <Nav></Nav>
    <Busca></Busca>
    <v-app>
      <v-main id="example-3">
        <div class="container">
          <div class="row">
            <div class="col-lg-12">
              <div class="form-inline">
                <v-text-field label="Divirta-se!" :value="search" v-on:keyup.enter="pesquisa" id="input-search-principal" v-model="search" placeholder="Divirta-se" hide-details="auto" class="input-search-relative">
                </v-text-field>
                <!-- <button v-on:click="envia" class="btn btn-outline-success my-2 my-sm-0">Search</button> -->
              </div>
              <br>
              <div id="trazer-gifs">

              </div>
            </div>
          </div>
        </div>
      </v-main>
    </v-app>
    <Footer></Footer>
  </div>

</template>

<script>
  import Nav from './components/Nav';
  import Busca from './components/Busca';
  import Footer from './components/Footer';

  export default {
    name: "App",
    components: {
      Nav,
      Busca,
      Footer
    },
    data() {
      return {
        search: ' '
      }
    },
    methods: {
      pesquisa: function() {
        var userInput = this.search;
        console.log(userInput);

        var giphyAPIKey = "iFH6GlogTVgIBunIN0Om1KtBqKITlPZu"
        var giphyAPIUrl = `https://api.giphy.com/v1/gifs/search?q=${userInput}&rating=g&api_key=${giphyAPIKey}`

        fetch(giphyAPIUrl).then(function (data) {
          return data.json()
        })
        .then(function (json) {
          console.log(json.data[0].images.fixed_height.url)
          var imgPath = json.data[0].images.fixed_height.url
          var img = document.createElement('img')
          img.setAttribute("src", imgPath)
          document.getElementById('trazer-gifs').appendChild(img)
        })

      }
     
    }
  };
</script>