<script context="module">
    export async function load({fetch,params }) {
        const res = await fetch(`https://api.themoviedb.org/3/search/movie?api_key=fd31484f9bb0e4c23be27ce18e09a0b5&language=en-US&query=${params.id}&page=1&include_adult=true`);
        const data = await res.json();
        if(res.ok){
            return{
                props: {searchedMovies: data.results }
            };
        }
    }
</script>

<script>
    import MovieCard from '../../components/MovieCard.svelte';
    export let searchedMovies;
</script>

<div class="searched-movies">
    {#each searchedMovies as movie}
    <MovieCard {movie}/>
    {/each}
</div>
<style>
    .searched-movies {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        grid-column-gap: 1rem;
        grid-row-gap: 2rem;
        height: 20vh;

    }
</style>