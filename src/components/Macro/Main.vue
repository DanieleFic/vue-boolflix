<template>
    <div class="ms_lista">
        <Cerca
        @cerca="filtraFilm"/>
    </div>
</template>

<script>
import axios from "axios"
import Cerca from '../commons/cerca.vue'
export default {
    name: 'Main',
    props: {
    
    },
    components: {
        Cerca
    },
    data(){
        return{
            apiUrl: 'https://api.themoviedb.org/3/search/movie',
            movieArray: [],
        }
    },
    created() {
        this.getFilm();
    },
    methods: {
        getFilm(){
            axios.get(this.apiUrl, {
            params: {
            api_key:"be63dc6417cc951f2c485376b9ceedd3",
            query:"zorro" 
            }
        })
        .then( (payload) => {
            this.movieArray = payload.data;
            console.log(this.movieArray)
            
        })
        .catch(function (error) {
            console.log(error);
        })
        .then(function () {
            // always executed
        });  
        }
    },
        
    
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">


</style>
