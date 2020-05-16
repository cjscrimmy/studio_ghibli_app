<template lang="html">
    <div v-if="film" id="filmDetail">
            <div id="wrapper">
                <div id="text-adjust">
                    <h1>{{film.title}}</h1>

                    <p><u><strong>Description</strong></u> </p>
                    <p>{{film.description}}</p>

                    <p><u><strong>Director</strong></u> {{film.director}}</p>

                    <p><u><strong>Producer</strong></u> {{film.producer}}</p>

                    <p><u><strong>Released</strong></u> {{film.release_date}}</p>
                </div>
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
    #wrapper p u{
        color: rgb(48, 47, 47);
        margin-right: 24px;
    }
    #wrapper h1{
        text-align: center;
        color: rgb(9, 46, 114);
        text-transform: uppercase;
    }
    #wrapper p{
        font-size: 16pt;
    }
    #text-adjust{
        margin: 24px;
        padding: 5px;
    }
</style>