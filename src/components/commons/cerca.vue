<template>
    <div>
        <!--emit che passa dati dal figlio al padre//lo passiamo al componente Header  -->
        <input 
        type="text"
        class="ms_input"
        v-model.trim="inputText"
        @keyup.enter="$emit('cercafilm',inputText)"
        placeholder="Cerca Titoli ">

       <!--  <button
            type="submit"
            class="ms_button"
            @click.prevent="$emit('cercafilm',inputText)">
                Search
        </button> -->

    </div>
</template>

<script>
export default {
    name:"cerca",
    data() {
        return{
            inputText: ""
        }
    }
}

</script>

<style lang="scss" scoped>
    .ms_button{
    background-color:red;
    margin-left: 10px;
    border: 0;
    }

    .ms_input{
        border: 1px solid rgba(255, 255, 255, 0.603);
        background-color:black;
        color: white;
        margin: 0px 10px;
    }

    .search-box{
        position: relative;
        width: 250px;
    }


</style>

