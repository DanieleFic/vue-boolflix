<template>
    <div  class="ms_contenitore col-3">
        <div class="ms_poster" @click="visibilità = !visibilità" >
                <img class="ms_cover" v-if="!visibilità" :src="getImg()" alt="">
                <ul class="ms_ul" v-if="visibilità">
                    <li>Titolo originale:{{info2.original_name}}</li>
                    <li>Titolo:{{info2.name}}</li>
                    <li>Lingua:  <img :src="cambioBandiera()" alt=""> </li>
                    <li class="ms_overview">Overview:{{info2.overview}}</li>
                    <li >
                        <i v-for="element in getStelline2(voto)" :key="element.id" class="fas fa-star"></i>
                        <i v-for="element in (5-getStelline2(voto))" :key="element.id" class="far fa-star"></i>
                    </li>
                </ul>
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
                return require("../../assets/img/red-flag.png")
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
        
        img{
            width: 100%
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
        height: 300px;

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