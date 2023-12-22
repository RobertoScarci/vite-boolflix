<script>
    import SingleFilm from '../components/SingleFilm.vue';
    import { store } from '../js/store';
    import SingleTvSeries from './SingleTvSeries.vue';

    export default {
    name: "ListMedia",
    data() {
        return {
            store
        }
    },
    components: {
        SingleFilm,
        SingleTvSeries
    }
    }
</script>

<template>
    <div class="container-fluid">
        <div class="row justify-content-center" v-if="store.movieList.length > 0">
            <h4 class="text-white">ORIGINALI NETFLIX</h4>
            <SingleFilm v-for="movie in store.movieList" :movie="movie"/>
            <SingleTvSeries v-for="tv in store.tvList" :key="tv.id" :tv="tv"/>
        </div>
        <div class="row justify-content-center mt-5" v-else>
            <span class="text-center mt-5 fs-2 text-white">Search Movies or Tv Series!</span>
        </div>
    </div>
</template>

<style lang="scss" scoped>

div.row{
    margin: 0 .5rem;
}

</style>