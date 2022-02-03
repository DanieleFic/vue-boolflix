<template>
    <div>
        
        <ul>
            <li>Titolo originale:{{info2.original_name}}</li>
            <li>Titolo:{{info2.name}}</li>
            <li>Lingua:  <img :src="cambioBandiera()" alt=""> </li>
            <li>Voto:{{info2.vote_average}}</li>
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
        }
    }

}

</script>

<style scoped lang="scss">
    img{
        width: 15px;
        height: 15px;
        text-align: center;
    } 
</style>