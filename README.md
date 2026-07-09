<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PAK TRADE | Official Terminal</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        body { font-family: 'Plus Jakarta Sans', sans-serif; background: #020617; color: #fff; }
        .glass { background: rgba(15, 23, 42, 0.6); backdrop-filter: blur(20px); border: 1px solid rgba(255, 255, 255, 0.08); }
        .page { display: none; }
        .active-page { display: block; }
    </style>
</head>
<body class="pb-24">

    <!-- LOGIN PAGE -->
    <div id="loginPage" class="page active-page flex items-center justify-center min-h-screen p-6">
        <div class="glass p-8 rounded-[2rem] w-full max-w-sm text-center">
            <h2 class="text-2xl font-black text-blue-500 mb-6">PAK TRADE LOGIN</h2>
            <input type="text" placeholder="Username" class="w-full bg-slate-900 p-3 rounded-xl mb-4 border border-slate-700">
            <input type="password" placeholder="Password" class="w-full bg-slate-900 p-3 rounded-xl mb-6 border border-slate-700">
            <button onclick="showDashboard()" class="w-full bg-blue-600 py-3 rounded-xl font-bold">SIGN IN</button>
        </div>
    </div>

    <!-- MAIN DASHBOARD -->
    <div id="dashboardPage" class="page max-w-7xl mx-auto p-6 space-y-8">
        <nav class="flex justify-between items-center">
            <h1 class="text-2xl font-black text-blue-500">PAK TRADE<span class="text-white">.PRO</span></h1>
            <div class="flex gap-4">
                <button onclick="switchTab('home')" class="text-sm">Home</button>
                <button onclick="switchTab('about')" class="text-sm">Company</button>
                <button onclick="switchTab('team')" class="text-sm">Salary</button>
            </div>
        </nav>

        <!-- Dynamic Content -->
        <div id="homeContent" class="tab-content active-page">
            <div class="grid grid-cols-1 md:grid-cols-4 gap-6 mb-8">
                <div class="glass p-8 rounded-[2rem] lg:col-span-2">
                    <p class="text-slate-400 text-xs">BALANCE</p>
                    <h2 id="balance" class="text-5xl font-extrabold">0.000000</h2>
                </div>
                <button onclick="claimBonus()" class="glass p-8 rounded-[2rem] text-center border-yellow-500/30">
                    <i data-lucide="gift" class="mx-auto mb-2 text-yellow-500"></i>
                    <p class="text-xs">DAILY BONUS</p>
                </button>
            </div>

            <h3 class="text-xl font-bold mb-4">Mining Nodes (20+)</h3>
            <div id="nodeGrid" class="grid grid-cols-2 md:grid-cols-5 gap-4"></div>
        </div>

        <!-- COMPANY DETAILS TAB -->
        <div id="aboutContent" class="tab-content page glass p-8 rounded-[2rem]">
            <h2 class="text-2xl font-bold mb-4">Company Profile</h2>
            <p class="text-slate-400">Pak Trade LLC is a registered investment firm.</p>
            <div class="mt-4 space-y-2 text-sm">
                <p><strong>Reg ID:</strong> PT-9988-PK</p>
                <p><strong>Location:</strong> Rawalpindi, Business Center, Office 402</p>
                <p><strong>Status:</strong> Licensed & Verified</p>
            </div>
        </div>

        <!-- SALARY TAB -->
        <div id="teamContent" class="tab-content page glass p-8 rounded-[2rem]">
            <h2 class="text-2xl font-bold mb-4">Salary Portal</h2>
            <div class="flex gap-6">
                <div><p class="text-slate-400">Weekly</p><p class="text-xl font-bold text-blue-400">3,500 PKR</p></div>
                <div><p class="text-slate-400">Monthly</p><p class="text-xl font-bold text-green-400">15,000 PKR</p></div>
            </div>
        </div>
    </div>

    <script>
        // Navigation Logic
        function showDashboard() {
            document.getElementById('loginPage').classList.remove('active-page');
            document.getElementById('dashboardPage').classList.add('active-page');
        }

        function switchTab(tab) {
            document.querySelectorAll('.tab-content').forEach(t => t.style.display = 'none');
            document.getElementById(tab + 'Content').style.display = 'block';
        }

        // Generate 20 Nodes
        const grid = document.getElementById("nodeGrid");
        for(let i=1; i<=20; i++) {
            grid.innerHTML += `
            <div class="glass p-4 rounded-2xl text-center">
                <i data-lucide="cpu" class="mx-auto mb-2 text-blue-500"></i>
                <p class="text-[10px] font-bold">NODE ${i}</p>
                <button class="w-full mt-2 bg-white text-black text-[10px] py-1 rounded">BUY</button>
            </div>`;
        }
        lucide.createIcons();

        // Bonus Logic
        function claimBonus() {
            let b = parseFloat(document.getElementById("balance").innerText);
            document.getElementById("balance").innerText = (b + 50).toFixed(6);
            alert("50 PKR added to your balance, sweetie!");
        }

        // Mining
        setInterval(() => {
            let b = parseFloat(document.getElementById("balance").innerText);
            document.getElementById("balance").innerText = (b + 0.0005).toFixed(6);
        }, 1000);
    </script>
</body>
</html>
