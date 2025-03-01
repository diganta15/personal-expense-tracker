<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    const handleClick =()=>{
        console.log('click');
        dispatch('filter',item);
    }

    export let item;
   
    
</script>

<button on:click={handleClick}  class="bg-indigo-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded">
    {item}
</button>