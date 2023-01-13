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
      APIUrlFilm: 'https://api.themoviedb.org/3/search/movie',
      APIUrlTv: 'https://api.themoviedb.org/3/search/tv',
    }
  },
  methods:{
    getFilm(serchText) {
      axios.get(this.APIUrlFilm, {
        params: {
          api_key: '7192f8da7811ab852ce08d351e509894',
          query: serchText,
        }
      })
        .then((response) => {
          console.log(response.data.results);

          store.filmList = response.data.results
        })

    },
    getTv(serchText) {
      axios.get(this.APIUrlTv, {
        params: {
          api_key: '7192f8da7811ab852ce08d351e509894',
          query: serchText,
        }
      })
        .then((response) => {
          console.log(response.data.results);

          store.tvList = response.data.results
        })

    }

    

  },
  created() {
    // this.getFilm();
  }
}


</script>

<template>
 <AppHeader @serchNameFilm="getFilm" @serchNameTv="getTv" />
 <AppMain/>
</template>

<style>

</style>
