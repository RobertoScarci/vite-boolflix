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
                this.store.movieList = response.data.results;
            })
        },
        getTvSeries(query) {
            axios.get('https://api.themoviedb.org/3/search/tv', {
                params: {
                api_key: '2902af90259528a807e51aa892d65a46',
                query,
                language: 'it-IT'
                }
            })
            .then( response => {
                this.store.tvList = response.data.results;
            })
        }}
    }
</script>

<template>
    <nav class="navbar">
        <div class="container-fluid ">
            
            <div class="nav mb-3">
                <img src="https://image.tmdb.org/t/p/w342/wwemzKWzjKYJFfCeiB57q3r4Bcm.png" alt="" class="p-3">
                <span class="mt-4 active">Home</span>
                <span class="mt-4">Serie TV</span>
                <span class="mt-4">Film</span>
                <span class="mt-4">Originali</span>
                <span class="mt-4">Aggiunti di recente</span>
                <span class="mt-4">La mia lista</span>
            </div>
            <div class="d-flex mb-3" role="search">
                <input class="form-control me-3 pt-2" type="search" placeholder="Search" aria-label="Search" v-model="query" @keydown.enter="getFilm(query), getTvSeries(query)">
                <button class="btn btn-danger" @click="getFilm(query), getTvSeries(query)">Search</button>
            </div>
        </div>
    </nav>
</template>

<style lang="scss" scoped>
img{
    width: 20%;
    margin-right: 1rem;
}

div > span{
    margin-right: 1.5rem;
    color: #777777;
}

.active{
    color: white;
}

span:hover{
    color: white;
}

</style>