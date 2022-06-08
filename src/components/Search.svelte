<script>
    import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher();

    let searchTerm = "";

    const search = (e) => {
        if (searchTerm) {
            dispatch("search", { searchTerm });
        }else{
            dispatch('clearSearch', {})
        }
    };
</script>

<input
    on:keyup={search}
    type="text"
    placeholder="Search Your Movies"
    bind:value={searchTerm}
/>


<style>
    input{
        width: 100%;
    }
</style>