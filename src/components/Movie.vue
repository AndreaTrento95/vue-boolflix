<template>
  <div>
      
      <ul class="list-group">
          <li class="list-group-item">{{ movie.title || movie.name}}</li>
          <li class="list-group-item">{{ movie.original_title || movie.original_name }}</li>

            <li v-if="flags.includes(movie.original_language)" class="list-group-item">
                <img :src="require(`@/assets/img/${movie.original_language}.png`)" :alt="movie.original_language">
            </li>
            <li v-else class="list-group-item">Language: {{ movie.original_language }}</li>

          <li class="list-group-item">{{ movie.original_language }}</li>
          <li class="list-group-item">{{ movie.vote_average }}></li>
      </ul>

  </div>
</template>

<script>
export default {
    name: 'Movie',
    props:{
        movie: Object,
    },
    data(){
        return{
            flags:['it', 'en'],
        }
    }
}
</script>

<style lang="scss" scoped>
div{
    padding: 10px;
}
img{
    width: 50px;
}

</style>