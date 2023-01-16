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
            <input type="text" name="serchName" id="serchName" v-model="serchText" placeholder="Cerca" @keyup="$emit('serchNameFilm',serchText), $emit('serchNameTv',serchText)">
        </section>
    </header>
    
    
</template>

<style scoped>

@import url(../../node_modules/bootstrap);


section{
    background-color: black;
    padding: 2.5rem;
    text-align: end;
}

</style>
