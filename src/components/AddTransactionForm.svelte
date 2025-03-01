<script>
    import { createEventDispatcher } from "svelte";
    import { v4 as uuidv4 } from 'uuid';
    const dispatch = createEventDispatcher();

   let expenseObj = {
        description:"",
        category:"",
        amount:0
   }

   



    const handleSubmit = () =>{
        const obj = {
            uniqueId : uuidv4(),
            ...expenseObj
        }
       
        dispatch('add-expense',obj);
    }


</script>

<main>
    <div class="p-6">
        <h3 class="text-lg font-semibold mb-4">Add New Transaction</h3>
        <form class="space-y-4" on:submit|preventDefault={handleSubmit}>
            <input
                type="text"
                placeholder="Description"
                class="w-full p-2 border rounded-lg focus:ring-2 focus:ring-blue-500 outline-none"
                bind:value={expenseObj.description} 
            />

            <select
                class="w-full p-2 border rounded-lg focus:ring-2 focus:ring-blue-500 outline-none bg-white"
                bind:value={expenseObj.category}
            >
                <option value="" disabled selected>Select Category</option>
                <option value={"Groceries"}>Groceries</option>
                <option value={"Transportation"}>Transportation</option>
                <option value={"Entertainment"}>Entertainment</option>
                <option value={"Utilities"}>Utilities</option>
                <option value={"Shopping"}>Shopping</option>
                <option value={"Healthcare"}>Healthcare</option>
                <option value={"Education"}>Education</option>
                <option value={"Income"}>Income</option>
            </select>

            <div class="flex gap-4">
                <input
                    type="number"
                    placeholder="Amount"
                    class="flex-1 p-2 border rounded-lg focus:ring-2 focus:ring-blue-500 outline-none"
                     bind:value={expenseObj.amount}
                />
            </div>

            <button
                class="w-full bg-blue-600 text-white py-2 rounded-lg hover:bg-blue-700 transition"

            >
                Add Transaction
            </button>
        </form>
    </div>
</main>
