<template>
    <div class="header">
        <div class="ms_boxheader">
            <div class="ms_logo">
                <img src="../../assets/img/LogoBoolFlix.png" alt="">
            </div>
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
    data: function () {
        return{
            logo: null
        }
    
    },
    methods: {
        //riceviamo i dati che ci arrivano dal figlio cerca con la funzione passaFiltro
        //passa filtro è il nome che diamo che poi dobbiamo richiamare nella nostra chiamata dati 
        passaFiltro(inputFiltro){//nelle parentesi ci arrivano i nostri dati e gli diamo un nome
            this.$emit("filtraAncora", inputFiltro)
            /* console.log("attivato passaggio in header") */
        },
        /* GetLogo(){
            return this.logo = "../../assets/img/LogoBoolFlix.png"
        } */
    }
}
</script>

<style scoped lang="scss">
    .header{
        height: 100px;
        background-color: black;
    
        .ms_boxheader{
            margin: 0 auto;
            width: 100%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            color: rgb(248, 0, 0);

            .ms_logo img{
                width: 250px;
                margin: 5px 10px;
            }
            
        }
    }
</style>