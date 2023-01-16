<script>
import { store } from '../store'



export default {
    data() {
        return {
            store,
            urlImg: 'https://flagcdn.com/96x72/',
            urlCopertina: 'https://image.tmdb.org/t/p/',
            urlDimensioneCopertina: 'w342',
            overIndex: 0,
            arrayGeneriTv: [],
        }
    },
    props: {
        titoloTv: String,
        titoloOriginaleTv: String,
        linguaTv: String,
        votoTv: Number,
        urlCopertinaTv: String,
        overviewTv: String,
        genresIdTv: Array,
    },
    methods: {
        getRating(voto) {

            const numeroStelle = Math.ceil(voto / 2);

            return numeroStelle;
        },
        getGenres() {
            const arrayId = [];



            store.genresTvList.forEach(element => {

                arrayId.push(element.id)

            });

            for (let index = 0; index < this.genresIdTv.length; index++) {


                const id = this.genresIdTv[index]

                const idTv = (element) => element == id;

                this.arrayGeneriTv.push(store.genresTvList[arrayId.findIndex(idTv)].name)

            }


        }

    },
    created() {
        this.getGenres();
    }
    
}

</script>

<template>

    <div class="copertina" :class="urlCopertinaTv == null ? `dNone` : ``, genresIdTv.includes(store.genresSelect) ? `` : store.genresSelect == 0 ? `` : `dNone`" @mouseover="this.overIndex = 1" @mouseleave="this.overIndex = 0">
        <img :src="urlCopertina + urlDimensioneCopertina + urlCopertinaTv" :alt="titoloTv">
        <div class="info" :class="overIndex == 1 ? `sfondoNero dBlock` : `dNone`">
            <p>Titolo: {{ titoloTv }}</p>
            <p :class="titoloTv == titoloOriginaleTv ? `dNone` : ``">Titolo originale: {{ titoloOriginaleTv }} </p>
            <p>Lingua: <img class="bandiera" :src="urlImg + linguaTv + '.png'" :alt="'Bandiera ' + linguaTv"> </p>
            <p>Voto:
                <font-awesome-icon :icon="getRating(votoTv) > 0 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />
                <font-awesome-icon :icon="getRating(votoTv) > 1 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />
                <font-awesome-icon :icon="getRating(votoTv) > 2 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />
                <font-awesome-icon :icon="getRating(votoTv) > 3 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />
                <font-awesome-icon :icon="getRating(votoTv) > 4 ? 'fa-solid fa-star' : 'fa-regular fa-star'" class="rating" />
            </p>
            <p :class="overviewTv == `` ? `dNone` : ``">Overview: {{ overviewTv.substring(0, 50)}} ...</p>
            <ul>
                <li>Genere:</li>
                <li v-for="genere in arrayGeneriTv">{{ genere }}</li>
            </ul>
        </div>
    </div>

</template>



<style scoped>
ul {
    color: white;
    list-style-type: none;
    margin: 0;
    padding: 0;
    display: flex;
    flex-wrap: wrap;

}

li {
    margin: 0.25rem;
}
.sfondoNero {
    background-color: black;
}

.dNone {
    display: none;
}

.dBlock {
    display: block;
}

p{
    margin: 0.25rem;
    color: white;
}

.rating {
    color: yellow;
}

.info {
    padding: 0.5rem;
    position: absolute;
    top: 0;
    width: 89%;
    height: 93%;
}
.copertina {
    width: calc(100% / 7 - 1rem);
    padding: 0.5rem;
    position: relative;
}

img {
  width: 100%;
}
.bandiera{
    width: 10%;
}
</style>
