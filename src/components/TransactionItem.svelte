<script>
    export let item
</script>

<main>
    <div class="flex justify-between items-center p-3 bg-gray-50 rounded-lg">
        <div>
            <p class="font-medium">{item.category}</p>
            <p class="text-sm text-gray-500">{item.description}</p>
        </div>
        <p class="text-red-600 font-medium">$ {item.amount}</p>
    </div>
</main>
