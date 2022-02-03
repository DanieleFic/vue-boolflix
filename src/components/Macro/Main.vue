<template>
    <div class="ms_lista">
        <Cerca
        @cercafilm="getFilm"/>
        <p v-if="movieArray.length > 1">FILM</p>
        <ListaFilm
            v-for="film in movieArray" 
            :key="film.id"
            :info="film"/>
            <p v-if="movieArray.length > 1">SERIE TV</p>
            <ListaSerie
            v-for="serie in serieTvArray" 
            :key="serie.id"
            :info2="serie"/>
    </div>
</template>

<script>
import axios from "axios"
import Cerca from '../commons/cerca.vue'
import ListaFilm from '../commons/ListaFilm.vue'
import ListaSerie from '../commons/ListaSerie.vue'
export default {
    name: 'Main',
    props: {
    
    },
    components: {
        Cerca,
        ListaFilm,
        ListaSerie
    },
    data(){
        return{
            apiUrlFilm: 'https://api.themoviedb.org/3/search/movie',
            apiUrlSerieTv: 'https://api.themoviedb.org/3/search/tv',
            movieArray: [],
            serieTvArray: [],
        }
    },
    
    methods: {
        getFilm(inputText){
            axios.get(this.apiUrlFilm, {
            params: {
            api_key:"be63dc6417cc951f2c485376b9ceedd3",
            query: inputText
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
            query: inputText
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
        
        
        
        /* filtraFilm(inputcerca){
            this.inputRicerca = inputcerca;
            console.log(this.inputRicerca)
        }, */
    },
    /* computed: {
        filmFiltrati(){
                return this.movieArray( () => {
                return this.inputRicerca = this.movieArray
                console.log('filtra personaggio');
                return film.name.toLowerCase().includes(this.inputRicerca.toLowerCase()); 
            });
            
        }
    },  */
        
    
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">


</style>
