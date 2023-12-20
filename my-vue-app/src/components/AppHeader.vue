<script>
    import { store } from '../js/store';
    import axios from 'axios';

    export default {
    name: "AppHeader",
    data() {
        return {
            store,
            query: '',
        }
    },
    methods: {
        getFilm(query) {
            axios.get('https://api.themoviedb.org/3/search/movie', {
                params: {
                api_key: '2902af90259528a807e51aa892d65a46',
                query,
                language: 'it-IT'
                }
            })
            .then( response => {
                console.log(response);
                this.store.movieList = response.data.results;
            })
            .catch(function (error) {
                console.log(error);
            }); 
        }
    }
    }
</script>

<template>
    <nav class="navbar mb-4">
        <div class="container-fluid bg-dark">
            <a class="navbar-brand text-danger fw-bold fs-2">BoolFlix</a>
            <div class="d-flex" role="search">
                <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" v-model="query" @keydown.enter="getFilm(query)">
                <button class="btn btn-danger" @click="getFilm(query)">Search</button>
            </div>
        </div>
    </nav>
</template>

<style lang="scss" scoped>

</style>