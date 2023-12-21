<script>
    import LangFlag from '../../node_modules/vue-lang-code-flags'

    export default {
    name: "SingleFilm",
    data() {
        return {
            currentFilm: []
        }
    },
    methods: {
        getStars(vote) {
            let stars = ""
            const starNumber = parseInt(vote / 2);
            for(let i=0; i < starNumber; i++) {
                stars += "★";
            }
            for(let i=0; i < 5 - starNumber; i++) {
                stars += "☆";
            }
            return stars;

        },
        getCast(id) {
            axios.get(`https://api.themoviedb.org/3/movie/${id}`, {
                params: {
                api_key: '2902af90259528a807e51aa892d65a46',
                language: 'it-IT',
                append_to_response: 'credits'
                }
            })
            .then( response => {
                this.currentFilm = response.data;
            })
        }
    },
    components: {
        LangFlag
    },
    props: {
        movie: {
            type: Object,
            required: true
        }
    }
    }
</script>

<template>
    <div class="col-2 mb-4 p-1">
        <img :src="(movie.poster_path != null) ? `http://image.tmdb.org/t/p/w342/${movie.poster_path}` : '/placeholder.jpg' " class="card-img-top " alt="...">
    </div>
</template>

<style lang="scss" scoped>

</style>