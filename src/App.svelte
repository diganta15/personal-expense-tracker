<script>
  import AddTransactionForm from "./components/AddTransactionForm.svelte";
  import TransactionList from "./components/TransactionList.svelte";

  export let expenses = [
    {
      uniqueId: "exp_001",
      amount: 85.5,
      category: "Groceries",
      description: "Weekly groceries from Walmart",
      date: new Date("2025-02-21"),
      type: "expense",
      paymentMethod: "Credit Card",
      isRecurring: false,
    },
    {
      uniqueId: "exp_002",
      amount: 45.0,
      category: "Transportation",
      description: "Uber ride to airport",
      date: new Date("2025-02-20"),
      type: "expense",
      paymentMethod: "Debit Card",
      isRecurring: false,
    },
    {
      uniqueId: "exp_003",
      amount: 3500.0,
      category: "Income",
      description: "Monthly Salary",
      date: new Date("2025-02-19"),
      type: "income",
      paymentMethod: "Bank Transfer",
      isRecurring: true,
    },
    {
      uniqueId: "exp_004",
      amount: 120.75,
      category: "Entertainment",
      description: "Movie tickets and dinner",
      date: new Date("2025-02-18"),
      type: "expense",
      paymentMethod: "Cash",
      isRecurring: false,
    },
    {
      uniqueId: "exp_005",
      amount: 251.0,
      category: "Utilities",
      description: "Electricity bill",
      date: new Date("2025-02-17"),
      type: "expense",
      paymentMethod: "Online Banking",
      isRecurring: true,
    },
  ];
    let  cnt = 0;
  
  expenses.map((ex)=>{
     cnt += ex.amount
  });

  $: totalExpense = expenses.length>0?(cnt):0
  console.log(totalExpense);

  let categories = [
    "Groceries",
    "Transportation",
    "Income",
    "Entertainment",
    "Utilities",
    "Shopping",
    "Healthcare",
    "Education",
  ];

  let addTransaction = (e) => {
    const newExpense = e.detail;
    cnt +=newExpense.amount;
    expenses = [newExpense,...expenses];

  };
</script>

<main>
  <!-- Main Container -->
  <div class="min-h-screen bg-gray-100 p-8">
    <!-- Dashboard Container -->
    <div class="max-w-4xl mx-auto bg-white rounded-lg shadow-lg">
      <!-- Header -->
      <div class="p-6 border-b border-gray-200">
        <h1 class="text-2xl font-bold text-gray-800">Expense Tracker</h1>
        <p class="text-gray-600">Track your daily expenses</p>
      </div>


      <div class="p-6 bg-blue-50 m-6 rounded-lg">
        <h2 class="text-lg font-semibold text-gray-700">Expenses</h2>
        <p class="text-3xl font-bold text-red-600">{totalExpense}</p>
      </div>

   

      <AddTransactionForm on:add-expense={addTransaction}/>

      <!-- Recent Transactions -->
      <div class="p-6">
        <h3 class="text-lg font-semibold mb-4">Recent Transactions</h3>
        <div class="space-y-3">
          <TransactionList {expenses} />
        </div>
      </div>
    </div>
  </div>
</main>
