<script>
    import { store } from '../store'



    export default {
        data() {
            return {
                store,
                urlImg: 'https://flagcdn.com/96x72/',
            }
        },
        props:{
            titoloFilm : String,
            titoloOriginaleFilm: String,
            linguaFilm: String,
            votoFilm: Number,
        }
    }

</script>

<template>
    
    <div>
        <h4>
            {{ titoloFilm }} / {{ titoloOriginaleFilm }} / {{ linguaFilm }} <img  :src= "urlImg + linguaFilm + '.png'"  :alt= "'Bandiera ' + linguaFilm"> / {{ votoFilm }}
        </h4>
    </div>

</template>

<style scoped>

</style>
