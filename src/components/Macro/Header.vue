<template>
    <div class="header">
        <Cerca
        @cercafilm="passaFiltro"/>
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
        height: 150px;
        background-color: black;
    }
</style>