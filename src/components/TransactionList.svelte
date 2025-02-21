<script>
    import TransactionItem from "./TransactionItem.svelte";

    export let expenses = []
</script>

{#each expenses as ex(ex.uniqueId)}
    <TransactionItem item={ex} />
{/each}