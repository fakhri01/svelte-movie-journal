<script>
	import MovieInput from "./components/MovieInput.svelte";
	import MovieList from "./components/MovieList.svelte";
	import Search from "./components/Search.svelte";

	let movies = localStorage.getItem("movies")
		? JSON.parse(localStorage.getItem("movies"))
		: [];

	const submitMovie = (movie) => {
		const updatedMovies = [movie, ...movies];
		localStorage.setItem("movies", JSON.stringify(updatedMovies));
		movies = updatedMovies;
	};

	const clearSearch = () => {
		movies = localStorage.getItem("movies")
			? JSON.parse(localStorage.getItem("movies"))
			: [];
	};

	const search = (searchTerm) => {
		const tempMovies = localStorage.getItem("movies")
			? JSON.parse(localStorage.getItem("movies"))
			: [];

		movies = tempMovies.filter((movie) =>
			movie.title.toLowerCase().includes(searchTerm.toLowerCase())
		);
	};
</script>

<div class="main">
	<h1>Movie Journal</h1>
	<Search on:search={e => search(e.detail.searchTerm)} on:clearSearch />
	<MovieInput on:submit-movie={(e) => submitMovie(e.detail.movie)} />
	<MovieList {movies} />
</div>

<style>
	.main {
		max-width: 960px;
		padding: 1rem;
		margin: auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
		text-align: center;
	}
</style>
