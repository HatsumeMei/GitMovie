<template>
  <div>
      <h1>Upcoming Movies</h1>
      <div v-for="movie in movies" :key="movie.id">
          <router-link :to="`/detail/${movie.id}`"><h4>{{movie.title}}</h4></router-link>
          <p>{{movie.id}}</p>
          </div>

 </div>
</template>

<script>
import axios from 'axios'
export default {
    
    name:'Movies',
    data()
    {
        return {
            movies:[]
        }
    },
    mounted(){
    axios.get("https://api.themoviedb.org/3/movie/now_playing?api_key=3df205218b4378351effe0505c27c613&language=en-US&page=1")
    .then ( response =>{
        console.log(response)
        this.movies = response.data.results;
    })
    }
}
</script>

<style>

</style>