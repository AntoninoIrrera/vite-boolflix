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
      APIUrlGeneriFilm: 'https://api.themoviedb.org/3/genre/movie/list',
      APIUrlGeneriTv: 'https://api.themoviedb.org/3/genre/tv/list',
      APIUrlFlag: 'https://flagcdn.com/it/codes.json',

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

    },
    getGenresFilm(){
      axios.get(this.APIUrlGeneriFilm, {
        params: {
          api_key: '7192f8da7811ab852ce08d351e509894',
        }
      })
      .then((response) => {
        console.log(response.data.genres);

        store.genresFilmList = response.data.genres
      })

    },
    getGenrestv() {
      axios.get(this.APIUrlGeneriTv, {
        params: {
          api_key: '7192f8da7811ab852ce08d351e509894',
        }
      })
        .then((response) => {
          console.log(response.data.genres);

          store.genresTvList = response.data.genres
        })

    },
    getFlag(){
      axios.get(this.APIUrlFlag, {
        params: {
          
        }
      })
        .then((response) => {
          console.log(response.data);

          store.flagList = response.data;
          

          for (const key in store.flagList) {
          
            store.keyFlagList.push(key)
          }

        
        })

    }

    

  },
  created() {
    this.getGenresFilm();
    this.getGenrestv();
    this.getFlag();
  }
}


</script>

<template>
 <AppHeader @serchNameFilm="getFilm" @serchNameTv="getTv" />
 <AppMain/>
</template>

<style>
body{
  margin: 0;
  background-color: gray;
}
</style>
