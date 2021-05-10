<template>
  <div>
      <h1>Movie Detail</h1>
      <img :src="`https://image.tmdb.org/t/p/w500${detailObj.poster_path}`">
      <h2>{{detailObj.title}}</h2>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    name:'Detail',
    data(){
        return{
            id:this.$route.params.id,
            detailObj:{}
        }

    },
    mounted()
    {
        axios.get(`https://api.themoviedb.org/3/movie/${this.id}?api_key=3df205218b4378351effe0505c27c613&language=en-US`)
        .then ( response =>{
        console.log(response);
        this.detailObj = response.data
        console.log(response.data.poster_path);
        
    })
    }

}

</script>

<style>

</style>