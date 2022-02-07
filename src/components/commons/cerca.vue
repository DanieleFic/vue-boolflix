<template>
    <div>
        <input 
        type="text"
        class="ms_input"
        v-model.trim="inputText"
        @keyup.enter="$emit('cercafilm',inputText)">

        <button
            type="submit"
            class="ms_button"
            @click.prevent="$emit('cercafilm',inputText)">
                Search
            </button>

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
    background-color:red ;
    border: 1px solid white;
    border-radius: 5px;
    margin-left: 10px;
    }

    .ms_input{
        border-radius: 5px;
    }
</style>

