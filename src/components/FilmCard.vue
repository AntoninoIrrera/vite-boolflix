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
                arrayGeneriFilm: [],
            }
        },
        props:{
            titoloFilm : String,
            titoloOriginaleFilm: String,
            linguaFilm: String,
            votoFilm: Number,
            urlCopertinaFilm: String,
            overviewFilm: String,
            genresIdFilm: Array,
        },
        methods:{
            getRating(voto){
                
                const numeroStelle = Math.ceil(voto / 2);
                
                return numeroStelle;
            },
            getGenres(){
                const arrayId = [];
                


                store.genresFilmList.forEach(element => {
                    
                    arrayId.push(element.id)

               });

                for (let index = 0; index < this.genresIdFilm.length; index++) {
                
                   
                   const id = this.genresIdFilm[index]
                   
                   const idFIlm = (element) => element == id;
                   
                   this.arrayGeneriFilm.push(store.genresFilmList[arrayId.findIndex(idFIlm)].name)
                   
                }

                
            }

        },
        created(){
            this.getGenres();
        }
    }

</script>

<template>
    
    <div class="copertina" :class="urlCopertinaFilm == null ? `dNone` : ``, genresIdFilm.includes(store.genresSelect) ? `` : store.genresSelect == 0 ? `` : `dNone` " @mouseover="this.overIndex = 1" @mouseleave="this.overIndex = 0">
        <img :src="urlCopertina + urlDimensioneCopertina + urlCopertinaFilm" :alt=titoloFilm>
        
        <div class="info" :class="overIndex == 1 ? `sfondoNero dBlock` : `dNone`">
            <p>Titolo: {{ titoloFilm }}</p>
            <p :class="titoloFilm == titoloOriginaleFilm ? `dNone` : ``">Titolo originale: {{ titoloOriginaleFilm }}</p>
            <p v-if="store.keyFlagList.includes(linguaFilm)">Lingua:<img class="bandiera" :src="urlImg + linguaFilm + '.png'" :alt="'Bandiera ' + linguaFilm"></p>
            <p v-else>Lingua: {{ linguaFilm }} </p>
            <p>Voto:
                <font-awesome-icon v-for="n in 5" :icon="getRating(votoFilm) > n - 1 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />
            </p>
            <p :class="overviewFilm == `` ? `dNone` : ``">Overview: {{ overviewFilm.substring(0,50) }}...</p>
            <ul>
                <li>Genere:</li>
                <li v-for="genere in arrayGeneriFilm">{{ genere }}</li>
            </ul>
        </div>
    </div>

</template>


<style scoped>
ul{
    color: white;
    list-style-type: none;
    margin: 0;
    padding: 0;
    display: flex;
    flex-wrap: wrap;

}

li{
    margin: 0.25rem;
}

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
    margin: 0.25rem;
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
    width: 10%;
    vertical-align: middle;
    margin-left: 0.25rem;
}

img{
    width: 100%;
}
</style>
