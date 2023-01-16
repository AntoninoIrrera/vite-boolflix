<script>
import { store } from '../store'



export default {
    data() {
        return {
            store,
            urlImg: 'https://flagcdn.com/96x72/',
            urlCopertina: 'https://image.tmdb.org/t/p/',
            urlDimensioneCopertina: 'w342',
        }
    },
    props: {
        titoloTv: String,
        titoloOriginaleTv: String,
        linguaTv: String,
        votoTv: Number,
        urlCopertinaTv: String,
    },
    methods: {
        getRating(voto) {

            const numeroStelle = Math.ceil(voto / 2);

            return numeroStelle;
        }
    }
}

</script>

<template>

    <div>
        <img :src="urlCopertina + urlDimensioneCopertina + urlCopertinaTv" :alt="titoloTv">
        <h4>
            {{ titoloTv }} / {{ titoloOriginaleTv }} / {{ linguaTv }} <img :src="urlImg + linguaTv + '.png'" :alt="'Bandiera ' + linguaTv"> / {{ getRating(votoTv) }}
            <font-awesome-icon :icon="getRating(votoTv) > 0 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />
            <font-awesome-icon :icon="getRating(votoTv) > 1 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />
            <font-awesome-icon :icon="getRating(votoTv) > 2 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />
            <font-awesome-icon :icon="getRating(votoTv) > 3 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />
            <font-awesome-icon :icon="getRating(votoTv) > 4 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />
                      
        </h4>
    </div>

</template>

<style scoped>

</style>
