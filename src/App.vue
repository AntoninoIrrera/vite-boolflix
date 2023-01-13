<script>
import axios from 'axios'
import {store} from './store'

import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'

export default{
  components:{
    AppHeader,
    AppMain,
  },
  data(){
    return{
      store,
      APIUrl: 'https://api.themoviedb.org/3/search/movie',
    }
  },
  methods:{
    getFilm(serchText) {
      axios.get(this.APIUrl, {
        params: {
          api_key: '7192f8da7811ab852ce08d351e509894',
          query: serchText,
        }
      })
        .then((response) => {
          console.log(response.data.results);

          store.filmList = response.data.results
        })

    }
    

  },
  created() {
    // this.getFilm();
  }
}


</script>

<template>
 <AppHeader @serchNameFilm="getFilm(store.serchText)"/>
 <AppMain/>
</template>

<style>

</style>
