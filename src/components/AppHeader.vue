<script>
import {store} from '../store'

export default{
    data(){
        return{
            store,
        }
    }
}

</script>

<template>
    
    <header>
        <label for="serchName">Cerca</label>
        <input type="text" name="serchName" id="serchName" v-model="store.serchText">
        <a href="#" @click="$emit('serchNameFilm')">Invio</a>
    </header>


</template>

<style scoped>

</style>
