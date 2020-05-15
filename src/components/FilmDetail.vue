<template lang="html">
    <div v-if="film" id="filmDetail">
        <h2>{{film.title}}</h2>
        <p><strong>Description:</strong> {{film.description}}</p>
        <p><strong>Director:</strong> {{film.director}}</p>
        <p><strong>Producer:</strong> {{film.producer}}</p>
        <p><strong>Release Date:</strong> {{film.release_date}}</p>
    </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: 'film-detail',
    data(){
        return {
            film: null
        }
    },
    mounted(){
        eventBus.$on('film-selected', (film) => {
            this.film = film
        })
    }
}
</script>

<style>
    #flexBox{
        display: flex;
    }
</style>