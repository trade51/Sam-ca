<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Nexus Premium Trading Terminal</title>
  <!-- Tailwind CSS CDN for modern styling -->
  <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
  <style>
    body {
      background-color: #06090e;
      color: #e2e8f0;
      font-family: system-ui, -apple-system, sans-serif;
    }
    .glass {
      background: rgba(13, 20, 35, 0.75);
      backdrop-filter: blur(16px);
      border: 1px solid rgba(255, 255, 255, 0.03);
    }
    /* Custom scrollbar for dark terminal theme */
    ::-webkit-scrollbar {
      width: 4px;
    }
    ::-webkit-scrollbar-track {
      background: rgba(0,0,0,0.1);
    }
    ::-webkit-scrollbar-thumb {
      background: rgba(255,255,255,0.1);
      border-radius: 2px;
    }
  </style>
</head>
<body class="min-h-screen p-3 md:p-6 flex flex-col items-center">

  <!-- TOP HEADER PANEL WITH SECRET TAP TARGET LOGO -->
  <header class="w-full max-w-6xl flex justify-between items-center mb-4 p-4 glass rounded-2xl border border-slate-800/40">
    <div id="app-logo" onclick="handleLogoTap()" class="flex items-center gap-2.5 cursor-pointer select-none active:scale-95 transition-transform">
      <div class="w-9 h-9 rounded-xl bg-gradient-to-tr from-emerald-500 to-cyan-400 flex items-center justify-center font-bold text-black shadow-[0_0_20px_rgba(16,185,129,0.25)]">⚡</div>
      <div>
        <span class="font-extrabold text-lg tracking-wider bg-gradient-to-r from-emerald-400 to-cyan-400 bg-clip-text text-transparent">NEXUS</span>
        <span class="text-[10px] text-slate-500 block font-mono tracking-widest uppercase -mt-1">Terminal v2.0</span>
      </div>
    </div>
    <div class="text-right flex items-center gap-3">
      <div class="hidden sm:block">
        <span class="text-[10px] text-gray-500 block uppercase tracking-wider">Account Status</span>
        <span class="text-sm font-semibold text-emerald-400" id="user-display-name">Loading System...</span>
      </div>
      <div id="user-display-mobile" class="sm:hidden text-sm font-semibold text-emerald-400">Loading...</div>
    </div>
  </header>

  <!-- MAIN OPERATIONAL VIEW PLATFORM -->
  <main id="user-view" class="w-full max-w-6xl grid grid-cols-1 lg:grid-cols-4 gap-4">
    
    <!-- LEFT COLUMN: REAL-TIME INTERACTIVE CHART PLUGINS -->
    <div class="lg:col-span-3 flex flex-col gap-4">
      <div class="glass rounded-2xl p-4 flex flex-col justify-between min-h-[420px] relative overflow-hidden">
        <div class="flex justify-between items-start mb-3 z-10">
          <div>
            <div class="flex items-center gap-2">
              <span class="font-bold text-lg text-white">BTC / USDT</span>
              <span class="text-xs font-mono bg-emerald-500/10 text-emerald-400 px-1.5 py-0.5 rounded">LIVE</span>
            </div>
            <h2 class="text-2xl font-black text-emerald-400 mt-1" id="live-crypto-price">$94,250.00</h2>
          </div>
          <div class="text-right text-xs font-mono text-slate-400">
            <div>24h High: <span class="text-white">$95,110</span></div>
            <div>24h Low: <span class="text-white">$92,400</span></div>
          </div>
        </div>

        <!-- TradingView Embedded Interactive Widget Integration -->
        <div class="w-full h-[320px] rounded-xl overflow-hidden border border-slate-800/60">
          <iframe src="https://s.tradingview.com/widgetembed/?frameElementId=tradingview_chart&symbol=BINANCE%3ABTCUSDT&interval=5&hidesidetoolbar=1&symboledit=0&saveimage=1&toolbarbg=0b0e14&studies=%5B%5D&theme=dark&style=1&timezone=Etc%2FUTC&studies_overrides=%7B%7D&overrides=%7B%7D&enabled_features=%5B%5D&disabled_features=%5B%5D&locale=en" class="w-full h-full border-0"></iframe>
        </div>
      </div>

      <!-- BOTTOM ROW ROW INSIDE PANEL: TRANSACTIONS & EXCHANGE BALANCES -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <!-- Wallet Actions and Operations Box -->
        <div class="glass rounded-2xl p-5 flex flex-col justify-between">
          <div>
            <span class="text-xs text-slate-400 uppercase tracking-widest block mb-1">Available Account Portfolio Balance</span>
            <h3 class="text-3xl font-black text-white tracking-tight mb-4" id="balance-display">$0.00</h3>
            
            <div class="space-y-2.5">
              <div>
                <label class="text-[11px] text-slate-400 block mb-1 font-medium">Execution Amount (USDT)</label>
                <input type="number" id="tx-amount" placeholder="0.00" class="w-full bg-slate-950 border border-slate-800 rounded-xl px-4 py-2.5 text-white focus:outline-none focus:border-emerald-500 text-sm transition-colors font-mono">
              </div>
              <div class="flex gap-2 pt-1">
                <button onclick="submitRequest('deposit')" class="w-1/2 bg-emerald-500 hover:bg-emerald-600 text-black font-extrabold py-2.5 rounded-xl transition-all cursor-pointer active:scale-[0.98] text-sm">Deposit Fund</button>
                <button onclick="submitRequest('withdrawal')" class="w-1/2 bg-slate-900 hover:bg-slate-800 border border-slate-800 text-white font-bold py-2.5 rounded-xl transition-all cursor-pointer active:scale-[0.98] text-sm">Withdrawal</button>
              </div>
            </div>
          </div>
        </div>

        <!-- Simulated Trading Simulator Console Log Panel -->
        <div class="glass rounded-2xl p-5 flex flex-col justify-between">
          <div>
            <span class="text-xs text-slate-400 uppercase tracking-widest block mb-2">Live Execution Positions</span>
            <div class="border border-dashed border-slate-800 rounded-xl p-6 text-center text-xs text-slate-500 flex flex-col items-center justify-center min-h-[110px]">
              <p>⚡ No current trade contracts initialization profiles deployed on network infrastructure pools.</p>
            </div>
          </div>
          <p class="text-[10px] text-slate-500 text-center mt-2">Manual validation required for financial adjustments profiles accounts.</p>
        </div>
      </div>
    </div>

    <!-- RIGHT COLUMN: LIQUIDITY FLUIDITY LIVE ORDER BOOK LOGS -->
    <div class="glass rounded-2xl p-4 flex flex-col h-full min-h-[500px]">
      <h3 class="text-xs font-bold text-slate-400 uppercase tracking-wider mb-3 pb-2 border-b border-slate-800/60">📊 Real-time Liquidity Order Book</h3>
      <div class="grid grid-cols-2 text-[10px] text-slate-500 font-mono mb-2 px-1">
        <div>PRICE (USDT)</div>
        <div class="text-right">SIZE (BTC)</div>
      </div>
      
      <!-- Asks Selling Blocks -->
      <div id="orderbook-asks" class="flex flex-col-reverse gap-1 text-rose-400 font-mono text-xs mb-3">
        <!-- Populated via system loop -->
      </div>
      
      <!-- Live Center Spread Metrics ticker -->
      <div class="bg-slate-900/60 p-2 rounded-lg text-center font-bold text-sm my-2 border border-slate-800/40 text-white font-mono" id="center-spread-price">
        $94,250.00
      </div>

      <!-- Bids Buying Blocks -->
      <div id="orderbook-bids" class="flex flex-col gap-1 text-emerald-400 font-mono text-xs">
        <!-- Populated via system loop -->
      </div>
    </div>
  </main>

  <!-- HIDDEN EAGLE EYE ADMIN PASSCODE MODAL CONTROLLERS OVERRIDES -->
  <div id="admin-modal" class="hidden fixed inset-0 bg-black/85 backdrop-blur-md flex items-center justify-center z-50 p-4">
    <div class="glass max-w-sm w-full rounded-2xl p-6 shadow-2xl border border-emerald-500/10">
      <h3 class="text-base font-bold text-emerald-400 mb-1 flex items-center gap-2">👁️ Eagle Eye Terminal Override</h3>
      <p class="text-xs text-slate-400 mb-4 font-normal">Security verification credentials token required for absolute matrix administrative console deployment views.</p>
      <input type="password" id="admin-key-input" placeholder="••••••••" class="w-full bg-slate-950 border border-slate-800 rounded-xl px-4 py-3 text-white mb-4 focus:outline-none focus:border-emerald-500 text-center tracking-widest font-mono text-lg">
      <div class="flex gap-2">
        <button onclick="closeAdminModal()" class="w-1/2 bg-slate-900 text-slate-400 py-2.5 rounded-xl text-xs font-bold border border-slate-800">Cancel</button>
        <button onclick="verifyAdminKey()" class="w-1/2 bg-emerald-500 text-black font-black py-2.5 rounded-xl text-xs shadow-lg shadow-emerald-500/10">Verify Matrix</button>
      </div>
    </div>
  </div>

  <!-- FULL BACKEND OVERVIEW ADMIN MANAGEMENT VIEWPORT -->
  <div id="admin-view" class="hidden w-full max-w-6xl flex flex-col gap-4">
    <div class="w-full glass rounded-2xl p-4 flex justify-between items-center border border-red-500/20 shadow-xl">
      <div>
        <span class="inline-block bg-red-500/10 text-red-400 text-[9px] uppercase tracking-widest font-bold px-2 py-0.5 rounded-md mb-0.5">Operator Command Privileges</span>
        <h2 class="text-lg font-black text-white">Eagle Eye Core Console</h2>
      </div>
      <button onclick="exitAdminMode()" class="bg-slate-900 border border-slate-800 hover:bg-slate-800 text-xs px-3 py-2 rounded-xl text-slate-300 font-bold transition-colors cursor-pointer">Close Operator Shield</button>
    </div>

    <div class="grid grid-cols-1 lg:grid-cols-3 gap-4">
      <!-- Admin Decisions Processing Ledger Queue -->
      <div class="lg:col-span-2 glass rounded-2xl p-5 border border-slate-800/30">
        <h3 class="text-xs font-bold text-slate-300 mb-4 uppercase tracking-wider flex items-center gap-2">⏳ Actionable Transactions Registry</h3>
        <div id="admin-queue-list" class="space-y-2.5 max-h-[420px] overflow-y-auto pr-1">
          <p class="text-xs text-slate-500 italic">Network configurations operating clean. No transactions awaiting approval updates profiles.</p>
        </div>
      </div>

      <!-- Core Global Directory Users List view -->
      <div class="glass rounded-2xl p-5 border border-slate-800/30">
        <h3 class="text-xs font-bold text-slate-300 mb-4 uppercase tracking-wider flex items-center gap-2">👥 System Identity Registrations</h3>
        <div id="admin-user-list" class="space-y-2.5 max-h-[420px] overflow-y-auto pr-1">
          <!-- Users profile loops loaded dynamically -->
        </div>
      </div>
    </div>
  </div>

  <!-- CORE SCRIPTS ENGINE INTERACTIVE ROUTERS -->
  <!-- Firebase Deployment Modules Module Context Config -->
  <script type="module">
    import { initializeApp } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-app.js";
    import { getDatabase, ref, set, push, onValue, update } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-database.js";
    import { getAuth, signInWithPopup, GoogleAuthProvider, onAuthStateChanged, signOut } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-auth.js";

    // Dynamic Credentials configuration initialization variables matching live deployment
    const firebaseConfig = {
      apiKey: "AIzaSyBqtvNJW_HNv4H2EAzeAhNL-tiUjX1huEg",
      authDomain: "trade51-f64d5.firebaseapp.com",
      databaseURL: "https://trade51-f64d5-default-rtdb.firebaseio.com",
      projectId: "trade51-f64d5",
      storageBucket: "trade51-f64d5.firebasestorage.app",
      messagingSenderId: "38759095579",
      appId: "1:38759095579:web:013d72ab4b5183f99347be"
    };

    // Service initializations hooks
    const app = initializeApp(firebaseConfig);
    const db = getDatabase(app);
    const auth = getAuth(app);
    const googleProvider = new GoogleAuthProvider();

    let currentUser = null;
    let balanceListener = null;

    // --- Google Authentication Providers Logic handlers ---
    window.loginWithGoogle = function() {
      signInWithPopup(auth, googleProvider)
        .catch((error) => {
          console.error("Auth Engine Error Profile Trace:", error);
          alert("Authentication initialization failed: " + error.message);
        });
    };

    window.logoutUser = function() {
      signOut(auth).then(() => {
        alert("Session terminated securely.");
      });
    };

    // --- Dynamic Network Authentication Listener Status State Mapping ---
    onAuthStateChanged(auth, (user) => {
      const displayDesk = document.getElementById('user-display-name');
      const displayMob = document.getElementById('user-display-mobile');
      
      if (user) {
        currentUser = user;
        const profileStr = `${user.displayName || user.email} <button onclick="logoutUser()" class="text-[10px] text-rose-400 font-bold underline ml-1.5 cursor-pointer hover:text-rose-500">Logout</button>`;
        displayDesk.innerHTML = profileStr;
        displayMob.innerHTML = profileStr;
        
        const userRef = ref(db, `users/${user.uid}`);
        if (balanceListener) balanceListener();
        
        balanceListener = onValue(userRef, (snapshot) => {
          const data = snapshot.val();
          if (data) {
            document.getElementById('balance-display').innerText = `$${data.balance.toFixed(2)}`;
          } else {
            set(userRef, {
              id: user.uid,
              name: user.displayName || "Nexus Trader",
              email: user.email,
              balance: 1000.00
            });
          }
        });
      } else {
        currentUser = null;
        document.getElementById('balance-display').innerText = "$0.00";
        const loginBtn = `<button onclick="loginWithGoogle()" class="bg-gradient-to-r from-emerald-500 to-cyan-500 text-black font-extrabold text-[11px] px-3 py-1.5 rounded-xl cursor-pointer shadow-md transition-transform active:scale-95">Login Identity</button>`;
        displayDesk.innerHTML = loginBtn;
        displayMob.innerHTML = loginBtn;
      }
    });

    // --- End User Manual Transfer Request Actions ---
    window.submitRequest = function(type) {
      if (!currentUser) {
        alert("Authentication validation missing! Please execute credential login first.");
        return;
      }
      
      const amountInput = document.getElementById('tx-amount');
      const amount = parseFloat(amountInput.value);

      if (!amount || amount <= 0) {
        alert("Invalid monetary metrics parameters provided!");
        return;
      }

      const txRef = ref(db, 'transactions/');
      const newTxRef = push(txRef);
      
      set(newTxRef, {
        txId: newTxRef.key,
        userId: currentUser.uid,
        userName: currentUser.displayName || currentUser.email,
        type: type,
        amount: amount,
        status: "pending"
      }).then(() => {
        alert(`${type.toUpperCase()} contract profile routing logs pushed for administrator manual audit.`);
        amountInput.value = '';
      });
    };

    // --- Dynamic Network Admin Dashboard Synchronization Pipelines ---
    onValue(ref(db, 'transactions/'), (snapshot) => {
      const queueContainer = document.getElementById('admin-queue-list');
      queueContainer.innerHTML = '';
      const data = snapshot.val();
      
      let pendingCount = 0;
      if (data) {
        Object.keys(data).forEach(key => {
          const tx = data[key];
          if(tx.status === 'pending') {
            pendingCount++;
            const card = document.createElement('div');
            card.className = "p-3 bg-slate-950 rounded-xl border border-slate-900 flex justify-between items-center text-xs";
            card.innerHTML = `
              <div>
                <div class="font-bold text-white flex items-center gap-1.5">${tx.userName} <span class="text-[9px] text-slate-500 font-mono">(${tx.userId.substring(0,6)}...)</span></div>
                <div class="text-[10px] ${tx.type === 'deposit' ? 'text-emerald-400' : 'text-rose-400'} uppercase font-extrabold mt-0.5 tracking-wider font-mono">${tx.type} • $${tx.amount.toFixed(2)}</div>
              </div>
              <div class="flex gap-1.5">
                <button onclick="processTx('${tx.txId}', '${tx.userId}', '${tx.type}', ${tx.amount}, 'approved')" class="bg-emerald-500 hover:bg-emerald-600 text-black font-black text-[11px] px-3 py-1 rounded-lg cursor-pointer transition-colors">Approve</button>
                <button onclick="processTx('${tx.txId}', '${tx.userId}', '${tx.type}', ${tx.amount}, 'rejected')" class="bg-slate-900 border border-slate-800 text-rose-400 font-bold text-[11px] px-3 py-1 rounded-lg cursor-pointer transition-colors">Reject</button>
              </div>
            `;
            queueContainer.appendChild(card);
          }
        });
      }
      if(pendingCount === 0) {
        queueContainer.innerHTML = '<p class="text-xs text-slate-500 italic text-center py-4">Network configurations operating clean. No transactions awaiting approval updates profiles.</p>';
      }
    });

    onValue(ref(db, 'users/'), (snapshot) => {
      const userContainer = document.getElementById('admin-user-list');
      userContainer.innerHTML = '';
      const data = snapshot.val();
      if(data) {
        Object.keys(data).forEach(key => {
          const user = data[key];
          const div = document.createElement('div');
          div.className = "p-2.5 bg-slate-950/60 border border-slate-900 rounded-xl text-xs flex justify-between items-center";
          div.innerHTML = `
            <div>
              <p class="font-bold text-slate-200">${user.name}</p>
              <p class="text-[9px] font-mono text-slate-500">ID: ${user.id.substring(0,10)}...</p>
            </div>
            <span class="font-mono text-emerald-400 font-extrabold bg-emerald-500/5 px-2 py-1 rounded-md border border-emerald-500/10">$${user.balance ? user.balance.toFixed(2) : '0.00'}</span>
          `;
          userContainer.appendChild(div);
        });
      }
    });

    // --- Administrative Core Routing Operations Decision Ledger logic executors ---
    window.processTx = function(txId, userId, type, amount, nextStatus) {
      if(nextStatus === 'approved') {
        const userBalanceRef = ref(db, `users/${userId}/balance`);
        onValue(userBalanceRef, (snapshot) => {
          const currentBal = snapshot.val() || 0;
          let updatedBal = currentBal;
          if(type === 'deposit') updatedBal += amount;
          if(type === 'withdrawal') updatedBal -= amount;
          
          update(ref(db, `users/${userId}`), { balance: updatedBal });
        }, { onlyOnce: true });
      }
      
      update(ref(db, `transactions/${txId}`), { status: nextStatus });
    };
  </script>

  <!-- USER GESTURES AND INTERACTIVE SYSTEMS SIMULATIONS CONFIGS -->
  <script>
    let tapCount = 0;
    let lastTap = 0;
    const MASTER_KEY = "admin123"; // Aap chahein toh is key ko badal sakte hain

    // Secret gesture tracking matrix 
    function handleLogoTap() {
      const now = new Date().getTime();
      if (now - lastTap > 1500) {
        tapCount = 0; 
      }
      tapCount++;
      lastTap = now;

      if (tapCount === 5) {
        tapCount = 0;
        document.getElementById('admin-modal').classList.remove('hidden');
      }
    }

    function closeAdminModal() {
      document.getElementById('admin-modal').classList.add('hidden');
      document.getElementById('admin-key-input').value = '';
    }

    function verifyAdminKey() {
      const inputKey = document.getElementById('admin-key-input').value;
      if (inputKey === MASTER_KEY) {
        closeAdminModal();
        document.getElementById('user-view').classList.add('hidden');
        document.getElementById('admin-view').classList.remove('hidden');
      } else {
        alert("Authentication code validation failed. Absolute matrix entry access denied.");
        closeAdminModal();
      }
    }

    function exitAdminMode() {
      document.getElementById('admin-view').classList.add('hidden');
      document.getElementById('user-view').classList.remove('hidden');
    }

    // --- Dynamic Orderbook Liquid Simulation Loop Engine ---
    function generateOrderBookData() {
      const asksContainer = document.getElementById('orderbook-asks');
      const bidsContainer = document.getElementById('orderbook-bids');
      const centerSpread = document.getElementById('center-spread-price');
      const livePriceHeader = document.getElementById('live-crypto-price');
      
      if(!asksContainer || !bidsContainer) return;
      
      let basePrice = 94200 + Math.random() * 100;
      centerSpread.innerText = `$${basePrice.toFixed(2)}`;
      if(livePriceHeader) livePriceHeader.innerHTML = `$${basePrice.toFixed(2)} <span class="text-xs text-emerald-500 font-normal">+2.4%</span>`;

      asksContainer.innerHTML = '';
      bidsContainer.innerHTML = '';

      // Create Fake Selling Orders (Asks - Red)
      for(let i=1; i<=6; i++) {
        let price = basePrice + (i * (0.5 + Math.random()));
        let size = (Math.random() * 2).toFixed(4);
        asksContainer.innerHTML += `<div class="flex justify-between px-1 hover:bg-rose-500/5 py-0.5 rounded"><div>$${price.toFixed(2)}</div><div class="text-slate-400 text-right">${size}</div></div>`;
      }

      // Create Fake Buying Orders (Bids - Green)
      for(let i=1; i<=6; i++) {
        let price = basePrice - (i * (0.5 + Math.random()));
        let size = (Math.random() * 2).toFixed(4);
        bidsContainer.innerHTML += `<div class="flex justify-between px-1 hover:bg-emerald-500/5 py-0.5 rounded"><div>$${price.toFixed(2)}</div><div class="text-slate-400 text-right">${size}</div></div>`;
      }
    }

    // Trigger fast execution ticks simulations fluidly
    setInterval(generateOrderBookData, 1200);
    window.onload = generateOrderBookData;
  </script>
</body>
</html>
