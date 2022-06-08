<script>
    export let movies
</script>

{#each movies as movie (movie.title)}
    <div>
        <h3>{movie.title}</h3>
        <p>Your rating: {movie.rating}</p>
    </div>
    <hr>
{/each}


<style>
    div{
        text-align: left;
    }
</style>