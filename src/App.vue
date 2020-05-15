<template lang="html">
  <div id="app">
      <div id="banner">
      </div>
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
    height: 300px;
    
    color: white;
  }
</style>