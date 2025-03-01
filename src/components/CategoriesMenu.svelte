<script>
    import Button from "./Button.svelte";
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
    const handleALL = () =>{
        dispatch('all');
    }
    export let categories = [];
</script>

<main>
    <div class="flex justify-center">
        <button on:click={handleALL} class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-3 px-6 mb-6 rounded text-lg">
          All
        </button>
      </div>

    <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 m-6">
        {#each categories as category, index}
        <Button item={category} index={index} on:filter />
    {/each}
    </div>
</main>