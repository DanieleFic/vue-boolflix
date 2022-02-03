<template>
    <div>
        
        <ul>
            <li><img class="ms_cover" :src="getImg()" alt=""></li>
            <li><img :src="cambioBandiera()" alt=""></li>
            <li>Titolo originale:{{info2.original_name}}</li>
            <li>Titolo:{{info2.name}}</li>
            <li>Lingua:  <img :src="cambioBandiera()" alt=""> </li>
            <li>Voto: <img v-for="element in getStelline()" :key="element.id" :src="numero" alt=""></li>
        </ul>

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
            numeroArrotondato : "",
            numero:""
        }
    },
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
                return "https://image.tmdb.org/t/p/w342" + this.info2.poster_path

            }else{
                return require("../../assets/img/No_Image_Cover.jpg")
            }
        },
        getStelline(){
            for (let index = 0; index < (this.info2.vote_average /2).toFixed(0); index++) {
                this.numero = require("../../assets/img/star.png")
                console.log(this.info2.vote_average)
                return this.numero
            }
            /* this.numeroArrotondato = (this.info2.vote_average /2).toFixed(0);
            return this.numeroArrotondato */
            
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
        width: 342px;
    }
</style>