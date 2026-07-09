<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PAK TRADE | FINAL TERMINAL</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        body { background: #020617; color: white; font-family: 'Inter', sans-serif; }
        .glass { background: rgba(15, 23, 42, 0.4); backdrop-filter: blur(20px); border: 1px solid rgba(255, 255, 255, 0.08); }
    </style>
</head>
<body class="pb-12">
    <main class="max-w-5xl mx-auto p-6">
        <!-- Header -->
        <header class="flex justify-between items-center mb-10">
            <h1 class="text-3xl font-black text-blue-500">PAK TRADE</h1>
            <div class="glass px-4 py-2 rounded-full text-xs font-bold text-green-500">● SYSTEM ONLINE</div>
        </header>

        <!-- Stats -->
        <section class="glass p-8 rounded-[2rem] mb-10 text-center">
            <p class="text-slate-400 text-xs uppercase tracking-widest">Total Asset Value</p>
            <h2 class="text-5xl font-black mt-2">0.000000 <span class="text-lg font-medium text-slate-500">PKR</span></h2>
        </section>

        <!-- 20+ Nodes -->
        <h3 class="text-xl font-bold mb-6">Cloud Mining Infrastructure</h3>
        <div id="nodeGrid" class="grid grid-cols-2 md:grid-cols-5 gap-4"></div>

        <!-- Payment Methods -->
        <section class="mt-16">
            <h3 class="text-xl font-bold mb-6">Secure Deposit Methods</h3>
            <div class="grid md:grid-cols-3 gap-6">
                <div class="glass p-6 rounded-[2rem] border border-green-500/20">
                    <h4 class="font-bold">EasyPaisa</h4>
                    <p class="text-sm text-slate-400">0337-9827882</p>
                </div>
                <div class="glass p-6 rounded-[2rem] border border-red-500/20">
                    <h4 class="font-bold">JazzCash</h4>
                    <p class="text-sm text-slate-400">0370-5519562</p>
                </div>
                <div class="glass p-6 rounded-[2rem] border-blue-400/20">
                    <h4 class="font-bold">SadaPay</h4>
                    <p class="text-sm text-slate-400">Nazim.pro</p>
                </div>
            </div>
        </section>
    </main>

    <script>
        const grid = document.getElementById("nodeGrid");
        for(let i=1; i<=20; i++) {
            grid.innerHTML += `
            <div class="glass p-4 rounded-2xl hover:border-blue-500 transition-all text-center">
                <i data-lucide="cpu" class="mx-auto mb-2 text-blue-500"></i>
                <p class="text-[10px] font-bold">NODE ${i}</p>
                <p class="text-[10px] text-slate-400">Profit: ${i * 50} PKR</p>
                <button class="w-full mt-3 py-1.5 bg-blue-600 rounded-lg text-[10px] font-bold hover:bg-blue-500">BUY</button>
            </div>`;
        }
        lucide.createIcons();
    </script>
</body>
</html>
