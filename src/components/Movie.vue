<template>
  <div>
      
      <ul class="list-group">
          <li class="list-group-item">{{ movie.title }}</li>
          <li class="list-group-item">{{ movie.original_title || movie.original_name }}</li>
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
    }
}
</script>

<style lang="scss" scoped>
div{
    padding: 10px;
}

</style>