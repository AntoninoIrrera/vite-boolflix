<script>
import {store} from '../store'



export default{
    data(){
        return{
            store,
            serchText: '',
        }
    },
    methods:{
        prova(){
            console.log(store.genresSelect)
        }
    }
}

</script>

<template>
    
    <header>
        <section>
            <img src="https://image.tmdb.org/t/p/w342/wwemzKWzjKYJFfCeiB57q3r4Bcm.png" alt="logo Netflix">
        </section>
        <section>
            <label for="genres">Seleziona un genere</label>
            <select name="genres" id="genres" v-model="store.genresSelect" @change="prova()">
                <option value="0">Tutti</option>
                <option v-for="genresFilm in store.genresFilmList" :value=genresFilm.id>{{genresFilm.name}}</option>
                <option v-for="genresTv in store.genresTvList" :value=genresTv.id>{{ genresTv.name }}</option>
            </select>
        </section>
        <section>
            <input type="text" name="serchName" id="serchName" v-model="serchText" placeholder="Cerca" @keyup.enter="$emit('serchNameFilm',serchText), $emit('serchNameTv',serchText)">
            <a href="#" class="bottone" @click="$emit('serchNameFilm',serchText), $emit('serchNameTv',serchText)">Cerca</a>
        </section>
    </header>
    
    
</template>

<style scoped>
a{
    text-decoration: none;
    color: white;
    margin-left: 2rem;
}

label{
    color: white;
    margin-right: 0.5rem;
}

input{
    height: 35px;
    width: 250px;
}

.bottone{
    border: 2px solid red;
    padding: 0.50rem 1rem;
    background-color: red;
}

header{
    background-color: black;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

section{
    padding: 2.5rem;
}
</style>
