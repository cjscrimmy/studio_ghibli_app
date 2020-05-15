<template lang="html">
    <div v-if="film" id="filmDetail">
        <div id="wrapper">
            <h2>{{film.title}}</h2>
            <p><strong>Description:</strong> {{film.description}}</p>
            <p><strong>Director:</strong> {{film.director}}</p>
            <p><strong>Producer:</strong> {{film.producer}}</p>
            <p><strong>Release Date:</strong> {{film.release_date}}</p>
        </div>
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
    #filmDetail{
        height: 250px;
        width: 100%;
        margin: 30px 0px 0px 0px;
        
    }

    #wrapper{
        align-content: center;
        justify-content: space-between;
        margin: 20px;
        background-color: rgb(201, 59, 15);
    }

    #wrapper p{
        color: white;
    }
    #wrapper p strong{
        color: rgb(48, 47, 47);
    }
    #wrapper h2{
        text-align: center;
        color: rgb(9, 46, 114);
    }
</style>