<template>
    <div class="ms_box">
        
        <h1 v-if="listaFilmArray.length != 0">Nuove Uscite Film</h1>
        <div class="containerflex">
            <!-- <div @click="scrollLeft" class="ms_scroll-left"><i class="bi bi-arrow-left"></i> </div> -->
            <div ref="scrollFilm" class="row">
                <div @click="scrollLeftFilm" class="ms_scroll-leftfilm"><i class="bi bi-arrow-left"></i> </div>
                <ListaFilm
                v-for="film in listaFilmArray" 
                :key="film.id"
                :info="film"/>
                <div @click="scrollRightFilm" class="ms_scroll-rightfilm"><i class="bi bi-arrow-right"></i> </div>
            </div>
            <!-- <div @click="scrollRight" class="ms_scroll-right"><i class="bi bi-arrow-right"></i> </div> -->
        </div>
        <h1 v-if="serieTvArray.length != 0">Nuove Uscite Serie Tv</h1>
        <div class="containerflex">
            
            <div ref="scrollSerie" class="row">
                <div @click="scrollLeftSerie" class="ms_scroll-leftserie"><i class="bi bi-arrow-left"></i> </div>
                <ListaSerie
                v-for="serie in serieTvArray" 
                :key="serie.id"
                :info2="serie"/>
                <div @click="scrollRightSerie" class="ms_scroll-rightserie"><i class="bi bi-arrow-right"></i> </div>
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
            scrollAmount: 0,
        }
    },
    
    methods: {
        scrollRightFilm(){
            let content = (this.$refs["scrollFilm"]);
            /* this.scrollTo(content, 300, 800); */
            content.scrollLeft += 400;
            console.log("ciao scroll right")
            /* setInterval(function () {
                this.scrollRight();
            }, 1000); */
        },

        scrollLeftFilm(){
            let content = (this.$refs["scrollFilm"]);
            /* this.scrollTo(content, 300, 800); */
            content.scrollLeft -= 400;
            console.log("ciao scroll left")
        },

        scrollRightSerie(){
            let content = (this.$refs["scrollSerie"]);
            content.scrollLeft += 400;
            console.log("ciao scroll right")
        },

        scrollLeftSerie(){
            let content = (this.$refs["scrollSerie"]);
            content.scrollLeft -= 400;
            console.log("ciao scroll left")
        }
    },
        /* filtraFilm(inputcerca){
            this.inputRicerca = inputcerca;
            console.log(this.inputRicerca)
        }, */

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
        overflow-y: hidden;
        overflow-x: hidden;
        background-color: RGB(19, 19, 19);
        padding-top:50px;
        height: calc(100vh - 50px);
        overflow-y: scroll;
        position: relative;
        &::-webkit-scrollbar {
                    display: none;
                }
        h1{
            margin: 0px 10px;
            color: rgb(255, 249, 249);
        }
        .containerflex{
            
            .row{
            white-space: nowrap;
            overflow-x: auto;
            white-space: nowrap;
            flex-direction: row;
            flex-wrap: nowrap;
            justify-content: flex-start;
            
                &::-webkit-scrollbar {
                    display: none;
                }
            }
        }

        .ms_scroll-leftfilm{
            position: absolute;
            top: 450px;
            width: 70px;
            left:15px;
            height: 5rem;
            background-color:rgba($color: #000000, $alpha: 0.7);

        }
        .ms_scroll-rightfilm{
            position: absolute;
            top: 450px;
            left:1830px;
            width: 70px;
            height: 5rem;
            background-color:rgba($color: #000000, $alpha: 0.7);

        }
        .ms_scroll-leftserie{
            position: absolute;
            top: 1250px;
            width: 70px;
            left:15px;
            height: 5rem;
            background-color:rgba($color: #000000, $alpha: 0.7);
        }
        .ms_scroll-rightserie{
            position: absolute;
            top: 1250px;
            left:1830px;
            width: 70px;
            height: 5rem;
            /* margin-left: 100px */;
            background-color:rgba($color: #000000, $alpha: 0.7);
        }
        .bi-arrow-right{
            color: red;
            font-size:45px;
            font-weight:bold;
        }
        .bi-arrow-left{
            color: red;
            font-size:45px;
            padding:5px;
            font-weight:bold;
        }
    }

</style>
