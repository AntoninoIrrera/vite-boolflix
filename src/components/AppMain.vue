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
            <FilmCard v-for="film in store.filmList" :urlCopertinaFilm="film.poster_path" :titoloFilm="film.title" :titoloOriginaleFilm="film.original_title" :linguaFilm="film.original_language" :votoFilm="film.vote_average" :overviewFilm="film.overview"/>
        </section>
        <section>
            <TvCard v-for="tv in store.tvList" :urlCopertinaTv="tv.poster_path" :titoloTv="tv.name" :titoloOriginaleTv="tv.original_name" :linguaTv="tv.original_language" :votoTv="tv.vote_average" :overviewTv="tv.overview"/>
        </section>
    </main>
  

</template>

<style scoped>
main{
    background-color: gray;
    margin-top: -21px;
}
section{
    display: flex;
    flex-wrap: wrap;
    padding: 0.5rem;
}
</style>
