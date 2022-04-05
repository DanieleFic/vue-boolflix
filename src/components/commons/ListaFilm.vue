<template>

    <div class="ms_contenitore col-3">
        <div class="ms_poster" @click="visibilità = !visibilità">
            
                <img class="ms_cover" v-if="!visibilità"  :src="getImg()" alt="">
                <ul class="ms_ul" v-if="visibilità">
                    <div>Titolo originale:{{info.original_title}}</div>
                    <div>Titolo:{{info.title}}</div>
                    <div>Lingua:  <img class="ms_bandiera" :src="cambioBandiera()" alt=""> </div>
                    <li class="ms_overview">Overview:{{info.overview}}</li>
                    <div>
                    <i v-for="element in getStelline2(voto)" :key="element.id" class="fas fa-star"></i>
                    <i v-for="element in (5-getStelline2(voto))" :key="element.id" class="far fa-star"></i>
                    </div>
                </ul>
            
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
                return require("../../assets/img/red-flag.png")
            }
        },
        getImg(){
            
            if(!this.info.poster_path == ""){
                return "https://image.tmdb.org/t/p/original" + this.info.poster_path
            }else{
                return require("../../assets/img/No_Image_Cover.jpg")
            }
        },
        
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
        height: 100%;
        width: 100%;
        
        img{
            width: 100%;
        }
    }

    .ms_poster{
        width: 500px;
        height: 700px;
        background-color: black;
        overflow-y: scroll;
    }

    .ms_poster::-webkit-scrollbar {
    display: none;
}

    .ms_contenitore{
        display: inline-block;
        float: none;
        margin: 10px 15px;
    }
    

    .ms_ul{
        padding:5px 5px;
        color: white;
        height: 100%;

        .ms_overview{
            font-size: 12px;
        }
        .fa-star{
                color: yellow;
            }
        li{
            list-style-type: none;

            
        }
    }

</style>