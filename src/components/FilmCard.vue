<script>
    import { store } from '../store'



    export default {
        data() {
            return {
                store,
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
            {{ titoloFilm }} / {{ titoloOriginaleFilm }} / {{ linguaFilm }} / {{ votoFilm }}
        </h4>
    </div>

</template>

<style scoped>

</style>
