<template>
  <div id="app">

    <Header 
      @startSearch="startSearch"
    />

    <Main v-if="results.movie.length > 0" type="movie" :list="results.movie" />
    <Main v-if="results.tv.length > 0" type="tv" :list="results.tv" />

  </div>
</template>

<script>

import Header from '@/components/Header';
import Main from '@/components/Main';
import axios from 'axios';


export default {
  name: "App",
  components: {
    Header,
    Main
  },
  data(){
    return{
      apiURL: 'https://api.themoviedb.org/3/search/',
      apiKey: '0eda15902ab6295f6f113373442b173e',
      results:{
        'movie':[],
        'tv': [],
      }
      
    }
  },
  methods:{

    startSearch(obj){
      this.resetResults();
      if(obj.type === 'all'){
        this.getAPI(obj.text, 'movie');
        this.getAPI(obj.text, 'tv');
      }else{
        this.getAPI(obj.text, obj.type);
      }
    },

    resetResults(){
      this.results.movie = [];
      this.results.tv = [];
    },

    getAPI(query, type){

      axios.get(this.apiURL+type,{
        params:{
          api_key: this.apiKey,
          query: query,
          language: 'it-IT'
        }
      })
      .then(res => {
        this.results[type] = res.data.results;
        console.log(res.data);
      })
      .catch(err => {
        console.log(err);
      })
    }
  },
  
};
</script>

<style lang="scss">
  @import '@/assets/styles/general';
</style>
