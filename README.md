<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Trade 1 | Investment Platform</title>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-900 text-white font-sans p-6">

    <!-- Header & Hidden Admin Trigger -->
    <header class="flex justify-between items-center mb-10">
        <div id="adminLogo" class="cursor-pointer">
            <h1 class="text-3xl font-bold text-blue-500">Trade 1</h1>
        </div>
        <div class="text-right">
            <p class="text-gray-400">Balance</p>
            <h2 class="text-2xl font-bold">0.00 PKR</h2>
        </div>
    </header>

    <!-- Deposit Section -->
    <section class="bg-gray-800 p-6 rounded-lg border border-gray-700 max-w-md mx-auto">
        <h3 class="text-xl font-bold mb-4">Investment Deposit</h3>
        
        <div class="space-y-4 text-gray-300 bg-gray-900 p-4 rounded mb-4">
            <p>Min Investment: <strong>300 PKR</strong></p>
            <p><strong>EasyPaisa:</strong> 0337-9827882</p>
            <p><strong>JazzCash/SadaPay:</strong> 0370-5519562</p>
            <p class="text-yellow-500 italic">Binance: Coming Soon!</p>
        </div>

        <form id="depositForm" class="space-y-3">
            <input type="text" id="tid" placeholder="Transaction ID (TID)" class="w-full bg-gray-900 p-2 rounded border border-gray-700" required>
            <input type="number" id="amount" placeholder="Amount (Min 300)" class="w-full bg-gray-900 p-2 rounded border border-gray-700" required>
            <button type="submit" class="w-full bg-green-600 hover:bg-green-700 p-2 rounded font-bold">Submit Payment</button>
        </form>
    </section>

    <script>
        // 1. Hidden Admin Access (Tap 5 times)
        let tapCount = 0;
        document.getElementById("adminLogo").addEventListener("click", () => {
            tapCount++;
            if (tapCount >= 5) {
                const key = prompt("Admin Key:");
                if (key === "5426") {
                    alert("Welcome to Trade 1 Admin Panel!");
                    window.location.href = "admin-dashboard.html";
                } else {
                    alert("Access Denied!");
                }
                tapCount = 0;
            }
        });

        // 2. Deposit Form Handler
        document.getElementById("depositForm").addEventListener("submit", (e) => {
            e.preventDefault();
            const amount = document.getElementById("amount").value;
            if (amount < 300) {
                alert("Minimum amount 300 PKR hai!");
            } else {
                alert("Deposit request pending mein chali gayi hai. Trade 1 admin review karega.");
            }
        });
    </script>
</body>
</html>
