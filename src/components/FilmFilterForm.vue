<template lang="html">
    <div id="formDiv">
        <form v-on:submit.prevent id="form">
            <span id="searchBox"><input type="text" v-model="search" placeholder="Search for a film" v-on:keyup="searchForFilm"/></span>
            <span id="dropdown"><select v-on:change="handleSelect" v-model="selectedFilm">
                <option disabled value="">Select a Film</option>
                <option v-for="film in films" :value="film">{{film.title}}</option>
            </select></span>

        </form>
    </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: 'film-filter-form',
    data() {
        return {
            "search": "",
            "selectedFilm": {}
        }
    },
    props: ["films"],
    methods: {
        searchForFilm(){
            let foundFilm = this.films.find((film) => {
                return film.title.toLowerCase().indexOf(this.search.toLowerCase()) > -1;
            })
            this.selectedFilm = foundFilm;

            eventBus.$emit('film-selected', this.selectedFilm)
        },
        handleSelect(){
            this.search ="";
            eventBus.$emit('film-selected', this.selectedFilm);
        }
    }
}
</script>

<style>
    #searchBox {
        padding: 0px;
        margin: 20px 20px 0px 0px;
    }
    #formDiv{
        display: block;
        text-align: center;
    }

    #form{
        display: inline-block;
        margin-right: auto;
        margin-left: auto; 
        text-align: left;
    }
</style>