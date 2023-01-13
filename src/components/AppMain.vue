<script>
    import {store} from '../store'

    import FilmCard from './FilmCard.vue'

    export default{
        components:{
            FilmCard,
        },
        data(){
            return{
                store,
            }
        }
    }

</script>

<template>
    <main>
        <section>
            <FilmCard v-for="film in store.filmList" :titoloFilm="film.title" :titoloOriginaleFilm="film.original_title" :linguaFilm="film.original_language" :votoFilm="film.vote_average"/>
        </section>
    </main>
  

</template>

<style scoped>

</style>
