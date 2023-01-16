<script>
    import { store } from '../store'



    export default {
        data() {
            return {
                store,
                urlCopertina: 'https://image.tmdb.org/t/p/',
                urlDimensioneCopertina: 'w342',
                urlImg: 'https://flagcdn.com/96x72/',
                overIndex: 0,
            }
        },
        props:{
            titoloFilm : String,
            titoloOriginaleFilm: String,
            linguaFilm: String,
            votoFilm: Number,
            urlCopertinaFilm: String,
            overviewFilm: String,
        },
        methods:{
            getRating(voto){
                
                const numeroStelle = Math.ceil(voto / 2);
                
                return numeroStelle;
            },

        }
    }

</script>

<template>
    
    <div class="copertina" @mouseover="this.overIndex = 1" @mouseleave="this.overIndex = 0">
        <img :src="urlCopertina + urlDimensioneCopertina + urlCopertinaFilm" :alt=titoloFilm>
        
        <div class="info" :class="overIndex == 1 ? `sfondoNero dBlock` : `dNone`">
            <p>Titolo: {{ titoloFilm }}</p>
            <p>Titolo originale: {{ titoloOriginaleFilm }}</p>
            <p>Lingua:<img class="bandiera" :src="urlImg + linguaFilm + '.png'" :alt="'Bandiera ' + linguaFilm"></p>
            <p>Voto:
                <font-awesome-icon :icon="getRating(votoFilm) > 0 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />
                <font-awesome-icon :icon="getRating(votoFilm) > 1 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />
                <font-awesome-icon :icon="getRating(votoFilm) > 2 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />
                <font-awesome-icon :icon="getRating(votoFilm) > 3 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />
                <font-awesome-icon :icon="getRating(votoFilm) > 4 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />
            </p>
            <p>Overview: {{ overviewFilm.substring(0,550) }}...</p>
        </div>
    </div>

</template>


<style scoped>

.sfondoNero{
    background-color: black;
}

.dNone{
    display: none;
}

.dBlock{
    display: block;
}

p{
    margin: 0;
    color: white;
}

.rating{
    color: yellow;
}

.info{
    padding: 0.5rem;
    position: absolute;
    top: 0;
    width: 89%;
    height: 93%;
    
}
.copertina{
    width: calc(100% / 7 - 1rem);
    padding: 0.5rem;
    position: relative;
}
   .bandiera{
    width: 20%;
   }
   img{
    width: 100%;
}
</style>
