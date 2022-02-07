<template>
    <div class="ms_contenitore col-3">
        <div class="ms_poster">
            <div @mouseover="visibilità = true" @mouseout="visibilità = false">
                <img v-if="!visibilità" class="ms_cover" :src="getImg()" alt="">
                <ul class="ms_ul" v-if="visibilità">
                    <div>Titolo originale:{{info.original_title}}</div>
                    <div>Titolo:{{info.title}}</div>
                    <div>Lingua:  <img class="ms_bandiera" :src="cambioBandiera()" alt=""> </div>
                    <div>
                    <i v-for="element in getStelline2(voto)" :key="element.id" class="fas fa-star"></i>
                    <i v-for="element in (5-getStelline2(voto))" :key="element.id" class="far fa-star"></i>
                    </div>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name:"ListaFilm",
    props: {
        info: Object
    },
    data() {
        return{
            voto:"",
            visibilità:false
        }
    },
    methods:{
        cambioBandiera(){
            if(this.info.original_language == "it"){
                return   require("../../assets/img/italy.png")

            }else if(this.info.original_language == "en"){
                return   require("../../assets/img/united-states.png")
            }else{
                return require("../../assets/img/flag.png")
            }
        },
        getImg(){
            return "https://image.tmdb.org/t/p/original" + this.info.poster_path
        },
        /* getStelline(){
            const arrayStelline = [];
            const numeroStelline = ( this.info.vote_average / 2).toFixed(0);
            for( let cont = 0; cont <= numeroStelline; cont++ )
            {
                arrayStelline.push( 2 )
            }
            return arrayStelline
        }, */
        getStelline2(){
            this.voto = Math.ceil( this.info.vote_average / 2)
            return this.voto
        }
    }

}

</script>

<style scoped lang="scss">
    .ms_bandiera{
        width: 15px;
        height: 15px;
        text-align: center;
    }

    .ms_cover{
        width: 100%
    }

    .ms_poster{
        width: 70%;
    }

    .ms_contenitore{
        margin: 10px 0px;
    }
    

    .ms_ul{
        padding:0;
        color: white;
        height: 300px;

        .fa-star{
                color: yellow;
            }
        li{
            list-style-type: none;

            
        }
    }

</style>