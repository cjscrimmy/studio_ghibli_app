<template lang="html">
    <div>
        <h2>Hi! I'm Film Filter Form</h2>
        <form v-on:submit.prevent>
            <select v-on:change="handleSelect" v-model="selectedFilm">
                <option disabled value="">Select a Film</option>
                <option v-for="film in films" :value="film">{{film.title}}</option>
            </select>

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
        handleSelect(){
            eventBus.$emit('film-selected', this.selectedFilm)
        }
    }
}
</script>

<style>

</style>