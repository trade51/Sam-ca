<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Eagle Eye Trading Terminal</title>
  <!-- Tailwind CSS CDN for modern styling -->
  <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
  <style>
    /* Sleek background with smooth transitions */
    body {
      background-color: #0b0e14;
      color: #e2e8f0;
      font-family: system-ui, -apple-system, sans-serif;
    }
    .glass {
      background: rgba(23, 29, 42, 0.65);
      backdrop-filter: blur(12px);
      border: 1px solid rgba(255, 255, 255, 0.05);
    }
  </style>
</head>
<body class="min-h-screen p-4 flex flex-col items-center">

  <!-- Header & Hidden Gesture Logo -->
  <header class="w-full max-w-4xl flex justify-between items-center mb-6 p-4 glass rounded-2xl">
    <div id="app-logo" onclick="handleLogoTap()" class="flex items-center gap-2 cursor-pointer select-none active:scale-95 transition-transform">
      <div class="w-8 h-8 rounded-lg bg-emerald-500 flex items-center justify-center font-bold text-black shadow-[0_0_15px_rgba(16,185,129,0.3)]">⚡</div>
      <span class="font-bold text-lg tracking-wider bg-gradient-to-r select-none from-emerald-400 to-cyan-400 bg-clip-text text-transparent">NEXUS TRADING</span>
    </div>
    <div class="text-right">
      <span class="text-xs text-gray-400 block">Account Status</span>
      <span class="text-sm font-semibold text-emerald-400" id="user-display-name">Loading System...</span>
    </div>
  </header>

  <!-- MAIN USER VIEW -->
  <main id="user-view" class="w-full max-w-4xl grid grid-cols-1 md:grid-cols-3 gap-6">
    <!-- Trading Chart Simulation Placeholder -->
    <div class="md:col-span-2 glass rounded-2xl p-6 min-h-[300px] flex flex-col justify-between">
      <div>
        <h3 class="text-gray-400 text-sm font-medium mb-1">BTC / USDT</h3>
        <h2 class="text-3xl font-extrabold text-emerald-400">$94,250.00 <span class="text-xs text-emerald-500 font-normal">+2.4%</span></h2>
      </div>
      <div class="h-32 flex items-end gap-1.5 pt-4">
        <!-- Mock bars for visual aesthetics -->
        <div class="w-full bg-emerald-500/20 h-1/3 rounded-t"></div>
        <div class="w-full bg-emerald-500/30 h-1/2 rounded-t"></div>
        <div class="w-full bg-rose-500/30 h-2/5 rounded-t"></div>
        <div class="w-full bg-emerald-500/40 h-3/4 rounded-t"></div>
        <div class="w-full bg-emerald-500/50 h-full rounded-t"></div>
      </div>
    </div>

    <!-- User Wallet & Manual Request Panel -->
    <div class="glass rounded-2xl p-6 flex flex-col justify-between">
      <div>
        <span class="text-xs text-gray-400 uppercase tracking-wider block mb-1">Your Total Balance</span>
        <h3 class="text-2xl font-bold text-white mb-6" id="balance-display">$0.00</h3>
        
        <div class="space-y-3">
          <div>
            <label class="text-xs text-gray-400 block mb-1">Amount (USDT)</label>
            <input type="number" id="tx-amount" placeholder="0.00" class="w-full bg-slate-900/80 border border-slate-700/50 rounded-xl px-4 py-2.5 text-white focus:outline-none focus:border-emerald-500 transition-colors">
          </div>
          <button onclick="submitRequest('deposit')" class="w-full bg-emerald-500 hover:bg-emerald-600 text-black font-bold py-2.5 rounded-xl transition-colors cursor-pointer">Request Deposit</button>
          <button onclick="submitRequest('withdrawal')" class="w-full bg-slate-800 hover:bg-slate-700 text-white font-bold py-2.5 rounded-xl border border-slate-700/50 transition-colors cursor-pointer">Request Withdrawal</button>
        </div>
      </div>
      <p class="text-[10px] text-gray-500 mt-4 text-center">Transactions require manual operator approval.</p>
    </div>
  </main>

  <!-- HIDDEN EAGLE EYE ADMIN PASSCODE MODAL -->
  <div id="admin-modal" class="hidden fixed inset-0 bg-black/80 backdrop-blur-sm flex items-center justify-center z-50 p-4">
    <div class="glass max-w-sm w-full rounded-2xl p-6 shadow-2xl border border-emerald-500/20">
      <h3 class="text-lg font-bold text-emerald-400 mb-2 flex items-center gap-2">👁️ Eagle Eye System</h3>
      <p class="text-xs text-gray-400 mb-4">Enter master security authentication token to initialize backend administrative terminal override.</p>
      <input type="password" id="admin-key-input" placeholder="Enter Secure Admin Key" class="w-full bg-slate-900 border border-slate-700 rounded-xl px-4 py-3 text-white mb-4 focus:outline-none focus:border-emerald-500 text-center tracking-widest">
      <div class="flex gap-2">
        <button onclick="closeAdminModal()" class="w-1/2 bg-slate-800 text-gray-300 py-2 rounded-xl text-sm">Cancel</button>
        <button onclick="verifyAdminKey()" class="w-1/2 bg-emerald-500 text-black font-bold py-2 rounded-xl text-sm shadow-lg shadow-emerald-500/20">Authenticate</button>
      </div>
    </div>
  </div>

  <!-- EAGLE EYE ADMIN CONTROL PANEL VIEW -->
  <div id="admin-view" class="hidden w-full max-w-4xl flex flex-col gap-6">
    <div class="w-full glass rounded-2xl p-4 flex justify-between items-center border border-red-500/20">
      <div>
        <span class="inline-block bg-red-500/10 text-red-400 text-[10px] uppercase tracking-widest font-bold px-2 py-0.5 rounded mb-1">Admin Mode Active</span>
        <h2 class="text-xl font-bold text-white">Eagle Eye Operator Console</h2>
      </div>
      <button onclick="exitAdminMode()" class="bg-slate-800 hover:bg-slate-700 text-xs px-3 py-1.5 rounded-xl text-gray-300 transition-colors">Exit Admin Panel</button>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
      <!-- Admin Control Transactions Queue -->
      <div class="md:col-span-2 glass rounded-2xl p-6">
        <h3 class="text-sm font-semibold text-gray-300 mb-4 flex items-center gap-2">📊 Pending Requests Queue</h3>
        <div id="admin-queue-list" class="space-y-3 max-h-[400px] overflow-y-auto pr-1">
          <p class="text-xs text-gray-500 italic">No transactions currently awaiting confirmation.</p>
        </div>
      </div>

      <!-- Complete User Database Visibility -->
      <div class="glass rounded-2xl p-6">
        <h3 class="text-sm font-semibold text-gray-300 mb-4 flex items-center gap-2">👥 Global User Directory</h3>
        <div id="admin-user-list" class="space-y-3 max-h-[400px] overflow-y-auto">
          <!-- Users dynamic profile load -->
        </div>
      </div>
    </div>
  </div>

  <!-- FIREBASE CONFIGURATION & DYNAMIC AUTH SYSTEM LOGIC -->
  <script type="module">
    import { initializeApp } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-app.js";
    import { getDatabase, ref, set, push, onValue, update } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-database.js";
    import { getAuth, signInWithPopup, GoogleAuthProvider, onAuthStateChanged, signOut } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-auth.js";

    // Aapki exact Firebase configuration credentials
    const firebaseConfig = {
      apiKey: "AIzaSyBqtvNJW_HNv4H2EAzeAhNL-tiUjX1huEg",
      authDomain: "trade51-f64d5.firebaseapp.com",
      databaseURL: "https://trade51-f64d5-default-rtdb.firebaseio.com",
      projectId: "trade51-f64d5",
      storageBucket: "trade51-f64d5.firebasestorage.app",
      messagingSenderId: "38759095579",
      appId: "1:38759095579:web:013d72ab4b5183f99347be"
    };

    // Initialize Services
    const app = initializeApp(firebaseConfig);
    const db = getDatabase(app);
    const auth = getAuth(app);
    const googleProvider = new GoogleAuthProvider();

    // Track state variables globally inside module context
    let currentUser = null;
    let balanceListener = null;

    // --- Google Login Trigger Function ---
    window.loginWithGoogle = function() {
      signInWithPopup(auth, googleProvider)
        .then((result) => {
          console.log("Logged in user:", result.user);
        })
        .catch((error) => {
          console.error("Login Error:", error);
          alert("Login failed: " + error.message);
        });
    };

    // --- Logout Function ---
    window.logoutUser = function() {
      signOut(auth).then(() => {
        alert("Logged out successfully!");
      });
    };

    // --- Dynamic Authentication State Listener ---
    onAuthStateChanged(auth, (user) => {
      const userDisplay = document.getElementById('user-display-name');
      
      if (user) {
        currentUser = user;
        userDisplay.innerHTML = `${user.displayName || user.email} <button onclick="logoutUser()" class="text-[10px] text-rose-400 underline ml-2 cursor-pointer">Logout</button>`;
        
        // Dynamic DB node reference setup matching user's real UID
        const userRef = ref(db, `users/${user.uid}`);
        
        if (balanceListener) balanceListener(); // purana listener clear karein
        
        balanceListener = onValue(userRef, (snapshot) => {
          const data = snapshot.val();
          if (data) {
            document.getElementById('balance-display').innerText = `$${data.balance.toFixed(2)}`;
          } else {
            // Naye user ke liye database entry banaen
            set(userRef, {
              id: user.uid,
              name: user.displayName || "Anonymous User",
              email: user.email,
              balance: 1000.00 // Default registration bonus
            });
          }
        });
      } else {
        currentUser = null;
        document.getElementById('balance-display').innerText = "$0.00";
        userDisplay.innerHTML = `<button onclick="loginWithGoogle()" class="bg-emerald-500 text-black font-bold text-xs px-3 py-1.5 rounded-xl cursor-pointer shadow-lg shadow-emerald-500/20">Login with Google</button>`;
      }
    });

    // --- Deposit & Withdrawal Request Handler ---
    window.submitRequest = function(type) {
      if (!currentUser) {
        alert("Please login first to request transitions!");
        return;
      }
      
      const amountInput = document.getElementById('tx-amount');
      const amount = parseFloat(amountInput.value);

      if (!amount || amount <= 0) {
        alert("Please enter a valid amount!");
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
        alert(`${type.toUpperCase()} request submitted for manual approval!`);
        amountInput.value = '';
      });
    };

    // --- Admin Side Panel Listeners ---
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
            card.className = "p-3 bg-slate-900/60 rounded-xl border border-slate-800 flex justify-between items-center";
            card.innerHTML = `
              <div>
                <div class="text-xs font-semibold text-white">${tx.userName}</div>
                <div class="text-[11px] ${tx.type === 'deposit' ? 'text-emerald-400' : 'text-rose-400'} uppercase font-bold mt-0.5">${tx.type} • $${tx.amount}</div>
              </div>
              <div class="flex gap-2">
                <button onclick="processTx('${tx.txId}', '${tx.userId}', '${tx.type}', ${tx.amount}, 'approved')" class="bg-emerald-500 text-black font-bold text-xs px-2.5 py-1 rounded-lg cursor-pointer">Approve</button>
                <button onclick="processTx('${tx.txId}', '${tx.userId}', '${tx.type}', ${tx.amount}, 'rejected')" class="bg-rose-500 text-white font-bold text-xs px-2.5 py-1 rounded-lg cursor-pointer">Reject</button>
              </div>
            `;
            queueContainer.appendChild(card);
          }
        });
      }
      if(pendingCount === 0) {
        queueContainer.innerHTML = '<p class="text-xs text-gray-500 italic">No transactions currently awaiting confirmation.</p>';
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
          div.className = "p-2.5 bg-slate-900/40 rounded-xl text-xs flex justify-between items-center";
          div.innerHTML = `
            <div>
              <p class="font-semibold text-gray-200">${user.name}</p>
              <p class="text-[10px] text-gray-500">ID: ${user.id}</p>
            </div>
            <span class="font-mono text-emerald-400 font-bold">$${user.balance ? user.balance.toFixed(2) : '0.00'}</span>
          `;
          userContainer.appendChild(div);
        });
      }
    });

    // --- Admin Transaction Decision Router ---
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

  <!-- GESTURE INTERACTION FLOW & PANEL VIEW CONTROLLERS -->
  <script>
    let tapCount = 0;
    let lastTap = 0;
    const MASTER_KEY = "admin123"; // Aap chahein toh is key ko change kar sakte hain

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
        alert("Invalid Master Key Authentication Failed!");
        closeAdminModal();
      }
    }

    function exitAdminMode() {
      document.getElementById('admin-view').classList.add('hidden');
      document.getElementById('user-view').classList.remove('hidden');
    }
  </script>
</body>
</html>
