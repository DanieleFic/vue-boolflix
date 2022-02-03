<template>
    <div>
        
        <ul>
            <li><img :src="getImg()" alt=""></li>
            <li>Titolo originale:{{info.original_title}}</li>
            <li>Titolo:{{info.title}}</li>
            <li>Lingua:  <img class="ms_bandiera" :src="cambioBandiera()" alt=""> </li>
            <li>Voto:{{info.vote_average}}</li>
        </ul>

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
            return "https://image.tmdb.org/t/p/w342" + this.info.poster_path
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


</style>