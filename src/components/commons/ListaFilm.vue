<template>
    <div>
        <ul>
            <li>Titolo originale:{{info.original_title}}</li>
            <li>Titolo:{{info.title}}</li>
            <li>Lingua:{{info.original_language}}</li>
            <li>Voto:{{info.vote_average}}</li>
        </ul>

    </div>
</template>

<script>
export default {
    name:"ListaFilm",
    props: {
        info: Object
    },
    data() {
        return{
            
        }
    }
}

</script>

<style>

</style>