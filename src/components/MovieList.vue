<template>
    <div id="movie-list">
        <div v-for="movie in filterMovies" class="movie">{{ movie.title }}</div>
    </div>
</template>

<script>
    import genres from '../util/genres';

    export default {
        data() {
            return {
                movies: [
                    { title: 'Kill BIll', genre: genres.ANIMATION },
                    { title: 'One home',  genre: genres.CRIME },
                    { title: 'Terminator',  genre: genres.COMEDY },
                ]
            }
        },
        props: ['genre' , 'time'],
        methods: {
            moviePassesGenreFilter(movie){
                if(!this.genre.length) {
                    return true;
                } else {
                    return this.genre.find(genre => movie.genre === genre);
                }
            }
        },
        computed: {
            filterMovies() {
                return this.movies.filter(this.moviePassesGenreFilter);
            }
        },
    }
</script>