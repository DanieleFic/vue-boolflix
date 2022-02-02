<template>
    <div class="ms_lista">
        <Cerca
        @cercafilm="getFilm"/>
        <ListaFilm
            v-for="film in movieArray" 
            :key="film.id"
            :info="film"/>
    </div>
</template>

<script>
import axios from "axios"
import Cerca from '../commons/cerca.vue'
import ListaFilm from '../commons/ListaFilm.vue'
export default {
    name: 'Main',
    props: {
    
    },
    components: {
        Cerca,
        ListaFilm
    },
    data(){
        return{
            apiUrl: 'https://api.themoviedb.org/3/search/movie',
            movieArray: [],
        }
    },
    
    methods: {
        getFilm(inputText){
            axios.get(this.apiUrl, {
            params: {
            api_key:"be63dc6417cc951f2c485376b9ceedd3",
            query: inputText
                }
            })
        .then( (payload) => {
            this.movieArray = payload.data.results;
            console.log("ciao",this.movieArray)
            
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
