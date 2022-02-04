<template>
    <div>
        
        <ul>
            <li><img :src="getImg()" alt=""></li>
            <li>Titolo originale:{{info.original_title}}</li>
            <li>Titolo:{{info.title}}</li>
            <li>Lingua:  <img class="ms_bandiera" :src="cambioBandiera()" alt=""> </li>
            <div ><i v-for="element in getStelline()" :key="element.id" class="fas fa-star"></i> </div>
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
        },
        getStelline(){
            const arrayStelline = [];
            const numeroStelline = ( this.info.vote_average / 2).toFixed(0);
            for( let cont = 0; cont <= numeroStelline; cont++ )
            {
                arrayStelline.push( 2 )
            }
            return arrayStelline
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