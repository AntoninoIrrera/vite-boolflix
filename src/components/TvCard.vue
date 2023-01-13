<script>
import { store } from '../store'



export default {
    data() {
        return {
            store,
            urlImg: 'https://flagcdn.com/96x72/',
        }
    },
    props: {
        titoloTv: String,
        titoloOriginaleTv: String,
        linguaTv: String,
        votoTv: Number,
    }
}

</script>

<template>

    <div>
        <h4>
            {{ titoloTv }} / {{ titoloOriginaleTv }} / {{ linguaTv }} <img :src="urlImg + linguaTv + '.png'" :alt="'Bandiera ' + linguaTv"> / {{ votoTv }}
        </h4>
    </div>

</template>

<style scoped>

</style>
