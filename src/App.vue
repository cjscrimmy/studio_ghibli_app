<template>
  <div>
    <h1>Hello Films</h1>
    <film-filter-form></film-filter-form>
    <film-detail></film-detail>
  </div>
</template>

<script>
import FilmFilterForm from './components/FilmFilterForm.vue';
import FilmDetail from './components/FilmDetail.vue'
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

</style>