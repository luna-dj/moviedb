<script context="module">
    export async function load({fetch}) {
        const res = await fetch(`https://api.themoviedb.org/3/movie/popular?api_key=fd31484f9bb0e4c23be27ce18e09a0b5&language=en-US&page=1`);
        const data = await res.json();
        if(res.ok){
            return{
                props: {popular: data.results }
            };
        }
    }
</script>

<script>
    import PopularMovies from "../components/PopularMovies.svelte";
    export let popular;
    import global from '../global.css';
    import SearchMovies from "../components/SearchMovies.svelte";
    import {fly} from 'svelte/transition';
</script>

<section in:fly={{y: 50, duration: 500, delay: 500}} out:fly={{duration: 500}}>
<SearchMovies />
<PopularMovies {popular} />
</section>