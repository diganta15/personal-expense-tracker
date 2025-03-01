<script>
    import TransactionItem from "./TransactionItem.svelte";

    export let exs = []
</script>

{#each exs as ex(ex.uniqueId)}
    <TransactionItem item={ex} />
{/each}