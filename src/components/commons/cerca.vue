<template>
    <div>
        <input 
        type="text"
        v-model.trim="inputText"
        @keyup="$emit('cercafilm',inputText)">

        <input
        type="button"
        value="Cerca"
        @click.prevent="$emit('filtra',inputText)">

    </div>
</template>

<script>
export default {
    name:"cerca"
}
</script>

<style>

</style>