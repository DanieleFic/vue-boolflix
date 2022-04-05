<template>
  <div id="app">
    <Header @filtraAncora="aggiornaDataAPI" />
    <Main :listaFilmArray="movieArray" :serieTvArray="serieTvArray" />
  </div>
</template>

<script>
import  Header from './components/Macro/Header.vue'
import  Main from './components/Macro/Main.vue'
import axios from "axios"
export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
    return{
      apiUrlFilm: 'https://api.themoviedb.org/3/search/movie',
      apiUrlSerieTv: 'https://api.themoviedb.org/3/search/tv',
      movieArray: [],
      serieTvArray: [],
      inputCercaAncora:""
    }
  },
  created: function(){
        this.FilmIniziali()
        
    },
  methods: {
      getFilm(){
        /* console.log("arrivato in main", this.inputCercaAncora) */
        axios.get(this.apiUrlFilm, {
          params: {
          api_key:"be63dc6417cc951f2c485376b9ceedd3",
          query: this.inputCercaAncora
          }
        })
        .then( (payload) => {
          this.movieArray = payload.data.results;
          console.log("filmArray",this.movieArray)
        })
        .catch(function (error) {
          console.log(error);
        })
        .finally(function () {
          console.log("prova");
        })
        
        axios.get(this.apiUrlSerieTv, {
        params: {
        api_key:"be63dc6417cc951f2c485376b9ceedd3",
        query: this.inputCercaAncora
        }
        })
        .then( (payload2) => {
          this.serieTvArray = payload2.data.results;
          console.log("serietvarray",this.serieTvArray)
        })
        .catch(function (error) {
          console.log(error);
        })
        .finally(function () {
          console.log("prova");
        })
        },
        //funzione che ti fa uscire i film alla creazione della pagina
        FilmIniziali: function(){
          this.inputCercaAncora = "The"
          this.getFilm()
          console.log("ciao")
          
        },
      /* passaFiltroApp(inputFiltro){
          this.$emit("filtraAncora", inputFiltro)
      }, */
      //dati che ci arrivano tramite emit dall Header
      aggiornaDataAPI(inputFiltro){
        this.inputCercaAncora = inputFiltro;
        this.getFilm()
        /* console.log("attivato passaggio in app", this.inputCercaAncora) */
        /* this.cercaFilm();
        this.cercaSerie(); */
        },
  }
}
</script>

<style lang="scss">
  @import "./assets/style/globals.scss";
  
</style>
