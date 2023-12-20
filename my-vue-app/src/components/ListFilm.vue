<script>
    import SingleFilm from '../components/SingleFilm.vue';
    import { store } from '../js/store';

    export default {
    name: "ListMedia",
    data() {
        return {
            store
        }
    },
    components: {
        SingleFilm
    }
    }
</script>

<template>
    <div class="container-fluid">
        <div class="row justify-content-center" v-if="store.movieList.length > 0">
            <SingleFilm v-for="movie in store.movieList" :movie="movie"/>
        </div>
        <div class="row justify-content-center mt-5" v-else>
            <span class="text-center mt-5 fs-2 text-white">Search Movies!</span>
        </div>
    </div>
</template>

<style lang="scss" scoped>

</style>