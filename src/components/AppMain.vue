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
        <div class="errore" v-if="store.filmList.length == 0 && store.tvList.length == 0">
            <h1>La ricerca non ha prodotto nessun risultato, si prega di inserire un nome coretto</h1>
        </div>
        <div v-else>
            <h1 v-if="store.filmList.length > 0">Film</h1>
            <section>
                <FilmCard v-for="film in store.filmList" :urlCopertinaFilm="film.poster_path" :titoloFilm="film.title" :titoloOriginaleFilm="film.original_title" :linguaFilm="film.original_language" :votoFilm="film.vote_average" :overviewFilm="film.overview" :genresIdFilm="film.genre_ids"/>
            </section>
            <h1 v-if="store.tvList.length > 0">Tv</h1>
            <section>
                <TvCard v-for="tv in store.tvList" :urlCopertinaTv="tv.poster_path" :titoloTv="tv.name" :titoloOriginaleTv="tv.original_name" :linguaTv="tv.original_language" :votoTv="tv.vote_average" :overviewTv="tv.overview" :genresIdTv="tv.genre_ids"/>
            </section>
        </div>
    </main>


</template>

<style scoped>
.errore{
    text-align: center;
    color: rgb(65, 0, 0);
}

h1{
   text-align: center;
}

section{
    display: flex;
    flex-wrap: wrap;
    padding: 0.5rem;
}
</style>
