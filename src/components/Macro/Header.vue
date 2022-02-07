<template>
    <div class="header">
        <div class="ms_boxheader">
            <h1>BoolFlix</h1>
            <Cerca
            @cercafilm="passaFiltro"/>
        </div>
    </div>
</template>

<script>
import  Cerca from "../commons/cerca.vue"


export default {
    name: 'Header',
    components: {
    Cerca
    },
    methods: {
        passaFiltro(inputFiltro){
            this.$emit("filtraAncora", inputFiltro)
            /* console.log("attivato passaggio in header") */
        }
    }
}
</script>

<style scoped lang="scss">
    .header{
        height: 50px;
        background-color: black;
    
        .ms_boxheader{
            margin: 0 auto;
            width: 80%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            color: rgb(248, 0, 0);
            
        }
    }
</style>