<template>
  <main class="container">
      <h1>{{ titles[type] }}</h1>
      
      <Movie 
        v-for="movie in list"
        :key="movie.id"
        :movie="movie"
      />
  </main>
</template>

<script>

import Movie from '@/components/Movie';

export default {
    name: 'Main',
    components: {
        Movie,
    },
    props:{
        type: String,
        list: Array
    },
    data(){
        return{
            titles:{
                'movie': 'Film trovati',
                'tv': 'Serie tv trovate'
            }
        }
    }
}
</script>

<style lang="scss" scoped>

</style>