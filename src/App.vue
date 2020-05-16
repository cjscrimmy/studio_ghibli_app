<template lang="html">
  <div id="app">
      <div id="banner">
        
      </div>
    
      <h1 id="site-title">Studio Ghibli Films App</h1>
      <film-filter-form :films="films" />
      <film-detail />
  </div>
</template>

<script>
import FilmFilterForm from './components/FilmFilterForm.vue';
import FilmDetail from './components/FilmDetail.vue';

export default {
  name: 'app',
  data(){
    return {
      films: []
    }
  },
  mounted(){
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(res => res.json())
    .then(films => this.films = films)
  },
  components: {
    'film-filter-form': FilmFilterForm,
    'film-detail': FilmDetail
  }

}
</script>

<style>
  #banner{
    background-image: url("assets/studio_ghibli_logo.png");
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-position-x: center;
    height: 300px;
    color: white;
  }
  #site-title{
    text-align: center;
    color: rgb(9, 46, 114);
    background: white;
  }
  body, html{
    height: 100%;
  }
  #app{
    background-image: url("assets/howlmc.jpg");

    height: 100%;

    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
  }

</style>