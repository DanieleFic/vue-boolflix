<template>
    <div class="ms_box">
        <h1 v-if="listaFilmArray.length != 0">FILM</h1>
        <div class="container">
            <div class="row">
                <ListaFilm
                v-for="film in listaFilmArray" 
                :key="film.id"
                :info="film"/>
            </div>
        </div>
        <h1 v-if="serieTvArray.length != 0">SERIE TV</h1>
        <div class="container">
            <div class="row">
                <ListaSerie
                v-for="serie in serieTvArray" 
                :key="serie.id"
                :info2="serie"/>
            </div>
        </div>
    </div>
</template>

<script>

import ListaFilm from '../commons/ListaFilm.vue'
import ListaSerie from '../commons/ListaSerie.vue'
export default {
    name: 'Main',
    components: {
        ListaFilm,
        ListaSerie
    },
    props: {
        listaFilmArray: Array,
        serieTvArray: Array
    },
    data(){
        return{
            
        }
    },
    
    methods: {
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
    
    .ms_box{
        background-color: rgb(73, 72, 72);
        padding-top:50px;
        height: calc(100vh - 50px);
        overflow-y: scroll;
        h1{
            text-align: center;
            color: white;
        }

        .row{
            display: flex;
            flex-direction: row;
            flex-wrap: wrap;
            justify-content: flex-start;
            
        }
    }

</style>
