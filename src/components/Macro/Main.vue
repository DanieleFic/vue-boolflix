<template>
    <div class="ms_main">
        
        <p v-if="listaFilmArray.length != 0">FILM</p>
            <ListaFilm
            v-for="film in listaFilmArray" 
            :key="film.id"
            :info="film"/>

            <p v-if="serieTvArray.length != 0">SERIE TV</p>
            <ListaSerie
            v-for="serie in serieTvArray" 
            :key="serie.id"
            :info2="serie"/>
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


</style>
