<script>
    import { store } from '../store'



    export default {
        data() {
            return {
                store,
                urlCopertina: 'https://image.tmdb.org/t/p/',
                urlDimensioneCopertina: 'w342',
                urlImg: 'https://flagcdn.com/96x72/',
                voto: 3,
            }
        },
        props:{
            titoloFilm : String,
            titoloOriginaleFilm: String,
            linguaFilm: String,
            votoFilm: Number,
            urlCopertinaFilm: String,
        },
        methods:{
            getRating(voto){
                
                const numeroStelle = Math.ceil(voto / 2);
                
                return numeroStelle;
            }
        }
    }

</script>

<template>
    
    <div class="copertina">
        <img :src="urlCopertina + urlDimensioneCopertina + urlCopertinaFilm" :alt=titoloFilm>
        <!-- <h4>
            {{ titoloFilm }} / {{ titoloOriginaleFilm }} / {{ linguaFilm }} <img  :src= "urlImg + linguaFilm + '.png'"  :alt= "'Bandiera ' + linguaFilm"> / {{ getRating(votoFilm) }}
            <font-awesome-icon :icon="getRating(votoFilm) > 0 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />
            <font-awesome-icon :icon="getRating(votoFilm) > 1 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />
            <font-awesome-icon :icon="getRating(votoFilm) > 2 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />
            <font-awesome-icon :icon="getRating(votoFilm) > 3 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />
            <font-awesome-icon :icon="getRating(votoFilm) > 4 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />            
        </h4> -->
    </div>

</template>

<style scoped>
.copertina{
    width: calc(100% / 7 - 1rem);
    padding: 0.5rem;
   }
   img{
    width: 100%;
}
</style>
