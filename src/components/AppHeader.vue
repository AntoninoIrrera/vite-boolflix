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
        <label for="serchName">Cerca</label>
        <input type="text" name="serchName" id="serchName" v-model="serchText">
        <a href="#" @click="$emit('serchNameFilm',serchText), $emit('serchNameTv',serchText)">Invio</a>
    </header>


</template>

<style scoped>

</style>
