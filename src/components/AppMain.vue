<script>
    import {store} from '../store'

    import FilmCard from './FilmCard.vue'
    import TvCard from './TvCard.vue'

    export default{
        components:{
            FilmCard,
            TvCard,
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
            <h1>Film:</h1>
            <FilmCard v-for="film in store.filmList" :urlCopertinaFilm="film.poster_path" :titoloFilm="film.title" :titoloOriginaleFilm="film.original_title" :linguaFilm="film.original_language" :votoFilm="film.vote_average"/>
        </section>
        <section>
            <h1>Tv:</h1>
            <TvCard v-for="tv in store.tvList" :urlCopertinaTv="tv.poster_path" :titoloTv="tv.name" :titoloOriginaleTv="tv.original_name" :linguaTv="tv.original_language" :votoTv="tv.vote_average"/>
        </section>
    </main>
  

</template>

<style scoped>

</style>
