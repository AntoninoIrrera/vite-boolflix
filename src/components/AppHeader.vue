<script>
import {store} from '../store'



export default{
    data(){
        return{
            store,
            serchText: '',
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

.bottone{
    border: 2px solid red;
    padding: 0.25rem 1rem;
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
