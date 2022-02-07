<template>
    <div  class="ms_contenitore col-3">
        <div class="ms_poster">
            <div @mouseover="visibilità = true" @mouseout="visibilità = false" >
                <img class="ms_cover" v-if="!visibilità" :src="getImg()" alt="">
                <ul class="ms_ul" v-if="visibilità">
                    <!-- <li><img :src="cambioBandiera()" alt=""></li> -->
                    <li>Titolo originale:{{info2.original_name}}</li>
                    <li>Titolo:{{info2.name}}</li>
                    <li>Lingua:  <img :src="cambioBandiera()" alt=""> </li>
                    <li >
                        <i v-for="element in getStelline2(voto)" :key="element.id" class="fas fa-star"></i>
                        <i v-for="element in (5-getStelline2(voto))" :key="element.id" class="far fa-star"></i>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name:"ListaSerie",
    props: {
        info2: Object
    },
    data() {
        return{
            voto:"",
            visibilità:false
        }
    },
    /* computed: {
        getStelline(){
            console.log((this.info2.vote_average / 2).toFixed(0))
            return (this.info2.vote_average / 2).toFixed(0)
        }
    }, */
    methods:{
        cambioBandiera(){
            if(this.info2.original_language == "it"){
                return   require("../../assets/img/italy.png")

            }else if(this.info2.original_language == "en"){
                return   require("../../assets/img/united-states.png")
            }else{
                return require("../../assets/img/flag.png")
            }
        },
        getImg(){
            
            if(!this.info2.poster_path == ""){
                return "https://image.tmdb.org/t/p/original" + this.info2.poster_path
            }else{
                return require("../../assets/img/No_Image_Cover.jpg")
            }
        },
        /* getStelline(){
            const arrayStelline = [];
            const numeroStelline = ( this.info2.vote_average/2);
            for( let cont = 0; cont < numeroStelline; cont++ )
            {
                arrayStelline.push( "☆" )
                console.log(arrayStelline)
            }
            return arrayStelline
        }, */
        getStelline2(){
            this.voto = Math.ceil( this.info2.vote_average / 2)
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
        height: 100%;
        width: 100%;
        border-radius:10px;
        img{
            width: 100%
        }
    }

    .ms_poster{
        width: 200px;
        height: 300px;
        background-color: black;
        border: 1px solid white;
        border-radius: 10px;
    }

    .ms_contenitore{
        padding: 10px 0px;
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