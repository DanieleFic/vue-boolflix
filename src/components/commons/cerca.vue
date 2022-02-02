<template>
    <div>
        <input 
        type="text"
        v-model.trim="inputText"
        @keyup.enter="$emit('cercafilm',inputText)">

        <button
            type="submit"
            class="btn btn-primary"
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

<style>

</style>