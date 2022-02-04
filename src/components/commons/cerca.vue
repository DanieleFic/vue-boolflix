<template>
    <div>
        <input 
        type="text"
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
    border-radius: 3px;
    }
</style>

