<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pak Trade Global LLC - Premium Network Platform</title>
    <style>
        /* Modern Glassmorphic Dark UI Theme */
        :root {
            --bg-base: #0a0e1a;
            --glass-surface: rgba(255, 255, 255, 0.03);
            --glass-border: rgba(255, 255, 255, 0.07);
            --glass-glow: rgba(255, 255, 255, 0.02);
            --neon-green: #00e676;
            --promo-red: #ff3e3e;
            --text-muted: #8492a6;
            --gold-warning: #f59e0b;
            --glow-green: rgba(0, 230, 118, 0.2);
        }

        body {
            background-color: var(--bg-base);
            background-image: 
                radial-gradient(circle at 10% 20%, rgba(0, 230, 118, 0.03) 0%, transparent 40%),
                radial-gradient(circle at 90% 80%, rgba(245, 158, 11, 0.02) 0%, transparent 40%);
            color: #e2e8f0;
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
            margin: 0;
            padding: 0;
            overflow-x: hidden;
        }

        /* 1. Live Notification Scrolling Ticker */
        .live-ticker-wrap {
            background: rgba(0, 230, 118, 0.05);
            border-bottom: 1px solid rgba(0, 230, 118, 0.12);
            padding: 10px 0;
            overflow: hidden;
            white-space: nowrap;
            position: sticky;
            top: 0;
            z-index: 1000;
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
        }

        .ticker-track {
            display: inline-block;
            animation: scrollTicker 30s linear infinite;
            font-size: 13px;
            font-weight: 600;
            color: var(--neon-green);
            text-shadow: 0 0 8px var(--glow-green);
        }

        @keyframes scrollTicker {
            0% { transform: translate3d(100%, 0, 0); }
            100% { transform: translate3d(-100%, 0, 0); }
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 30px 20px;
        }

        /* Top Navigation Header */
        .main-navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 40px;
            background: var(--glass-surface);
            border: 1px solid var(--glass-border);
            padding: 15px 25px;
            border-radius: 16px;
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
        }

        .nav-logo h2 { margin: 0; font-size: 22px; font-weight: 800; letter-spacing: 0.5px; color: #fff; }
        .nav-logo small { color: var(--text-muted); font-size: 11px; }

        /* Premium Glowing Logout Button */
        .logout-btn {
            background: rgba(255, 62, 62, 0.1);
            border: 1px solid rgba(255, 62, 62, 0.3);
            color: #ff6b6b;
            padding: 8px 18px;
            border-radius: 10px;
            font-weight: 600;
            font-size: 13px;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .logout-btn:hover {
            background: var(--promo-red);
            color: #fff;
            box-shadow: 0 0 15px rgba(255, 62, 62, 0.4);
            transform: translateY(-2px);
        }

        /* 2. User Stats Control Center (Glassmorphism Cards) */
        .dashboard-header {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 20px;
            margin-bottom: 35px;
        }

        .stat-box {
            background: var(--glass-surface);
            border: 1px solid var(--glass-border);
            box-shadow: inset 0 1px 1px rgba(255,255,255,0.05);
            border-radius: 20px;
            padding: 25px;
            text-align: center;
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            transition: transform 0.3s ease;
        }
        .stat-box:hover { transform: translateY(-3px); }
        .stat-box h4 { margin: 0; font-size: 11px; text-transform: uppercase; color: var(--text-muted); letter-spacing: 1px; }
        .stat-box p { margin: 10px 0 0 0; font-size: 28px; font-weight: 800; color: #fff; text-shadow: 0 2px 4px rgba(0,0,0,0.3); }

        /* 3. Operational Forms Flex Section */
        .operations-panel {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
            gap: 25px;
            margin-bottom: 40px;
        }

        .op-card {
            background: var(--glass-surface);
            border: 1px solid var(--glass-border);
            box-shadow: inset 0 1px 1px rgba(255,255,255,0.03);
            border-radius: 20px;
            padding: 25px;
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
        }

        .op-card h3 { margin-top: 0; font-size: 17px; color: #fff; display: flex; align-items: center; gap: 8px; font-weight: 700; }
        
        .input-group { margin-bottom: 20px; }
        .input-group label { display: block; font-size: 11px; color: var(--text-muted); margin-bottom: 6px; text-transform: uppercase; letter-spacing: 0.5px; }
        
        .input-group input, .input-group select {
            width: 100%;
            background: rgba(0, 0, 0, 0.4);
            border: 1px solid var(--glass-border);
            padding: 12px;
            border-radius: 10px;
            color: #fff;
            box-sizing: border-box;
            font-size: 14px;
            transition: all 0.3s ease;
        }

        .input-group input:focus, .input-group select:focus { 
            border-color: var(--neon-green); 
            box-shadow: 0 0 10px rgba(0, 230, 118, 0.15);
            outline: none; 
        }

        .form-action-btn {
            width: 100%;
            background: var(--neon-green);
            color: #0a0e1a;
            border: none;
            padding: 14px;
            border-radius: 10px;
            font-weight: 700;
            font-size: 14px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 12px rgba(0, 230, 118, 0.2);
        }
        .form-action-btn:hover { 
            opacity: 0.95; 
            box-shadow: 0 6px 18px rgba(0, 230, 118, 0.3);
            transform: translateY(-1px);
        }

        /* 4. Nodes Store Engine Layout */
        .section-title {
            font-size: 22px;
            font-weight: 800;
            margin: 50px 0 25px 0;
            border-left: 4px solid var(--neon-green);
            padding-left: 12px;
            color: #fff;
            text-shadow: 0 0 10px rgba(0, 230, 118, 0.1);
        }

        #nodes-display-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 25px;
        }

        .node-premium-card {
            background: var(--glass-surface);
            border: 1px solid var(--glass-border);
            border-radius: 24px;
            overflow: hidden;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
        }
        .node-premium-card:hover { 
            transform: translateY(-6px); 
            border-color: rgba(255,255,255,0.15);
            box-shadow: 0 12px 24px rgba(0,0,0,0.3);
        }

        .promo-active-border { border-color: rgba(255, 62, 62, 0.25) !important; }
        .promo-active-border:hover { border-color: rgba(255, 62, 62, 0.4) !important; }

        .node-image-wrap { position: relative; width: 100%; height: 150px; overflow: hidden; }
        .node-image-wrap img { width: 100%; height: 100%; object-fit: cover; transition: transform 0.5s ease; }
        .node-premium-card:hover .node-image-wrap img { transform: scale(1.05); }
        
        .node-badge-cost {
            position: absolute; bottom: 12px; right: 12px;
            color: #070a13; font-weight: 800; padding: 6px 12px;
            border-radius: 8px; font-size: 13px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
        }

        .promo-ribbon {
            position: absolute; top: 12px; left: 12px; background: var(--promo-red);
            color: #fff; font-size: 10px; font-weight: 900; padding: 4px 8px; border-radius: 6px;
            box-shadow: 0 4px 8px rgba(255, 62, 62, 0.3);
        }

        .node-meta-body { padding: 20px; }
        .node-meta-body h3 { margin: 0 0 15px 0; font-size: 18px; color: #fff; font-weight: 700; }
        .meta-row { display: flex; justify-content: space-between; font-size: 13px; color: var(--text-muted); margin-bottom: 8px; }

        .timer-box {
            display: flex; align-items: center; gap: 8px;
            background: rgba(0, 0, 0, 0.3); padding: 10px; border-radius: 12px; margin: 15px 0;
            border: 1px solid rgba(255,255,255,0.02);
        }
        .timer-text-wrap p { margin: 0; font-size: 13px; font-weight: 700; color: var(--gold-warning); font-family: monospace; letter-spacing: 0.5px; }
        
        .node-action-btn {
            width: 100%; background: transparent; border: 1px solid rgba(0,230,118,0.25);
            color: var(--neon-green); padding: 12px; border-radius: 12px; font-weight: 700; font-size: 13px; cursor: pointer;
            transition: all 0.3s ease;
        }
        .node-action-btn:hover { background: var(--neon-green); color: #0a0e1a; box-shadow: 0 4px 12px rgba(0,230,118,0.25); }
    </style>
</head>
<body>

    <!-- 1. Real-time Live Ticker Module -->
    <div class="live-ticker-wrap">
        <div class="ticker-track" id="payout-ticker">
            Initializing decentralized ledger secure array stream...
        </div>
    </div>

    <div class="container">
        <!-- Main Elegant Navbar -->
        <nav class="main-navbar">
            <div class="nav-logo">
                <h2>Pak Trade Global LLC</h2>
                <small>Terminal Core Infrastructure • trade51.github.io/Pak-trade/</small>
            </div>
            <!-- Logout Button UI Trigger Linked to Firebase Auth -->
            <button class="logout-btn" onclick="logoutUser()">
                <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M9 21H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h4"></path><polyline points="16 17 21 12 16 7"></polyline><line x1="21" y1="12" x2="9" y2="12"></line></svg>
                Logout
            </button>
        </nav>

        <!-- 2. Wallet Core Dashboard -->
        <div class="dashboard-header">
            <div class="stat-box">
                <h4>Available Capital Balance</h4>
                <p id="user-balance">Rs. 0</p>
            </div>
            <div class="stat-box">
                <h4>Total Affiliate Rewards</h4>
                <p id="user-referrals">Rs. 0</p>
            </div>
            <div class="stat-box">
                <h4>Active Running Nodes</h4>
                <p id="active-nodes-count">0</p>
            </div>
        </div>

        <!-- 3. Gateway Interaction Blocks -->
        <div class="operations-panel">
            <!-- Deposit Interface -->
            <div class="op-card">
                <h3>📥 Capital Gateway (Deposit)</h3>
                <form id="deposit-form" onsubmit="handleDeposit(event)">
                    <div class="input-group">
                        <label>Select Channel</label>
                        <select required>
                            <option value="easypaisa">EasyPaisa Official System</option>
                            <option value="jazzcash">JazzCash Instant Transfer</option>
                        </select>
                    </div>
                    <div class="input-group">
                        <label>Exact Value Amount (PKR)</label>
                        <input type="number" min="200" placeholder="Minimum Rs. 200" id="dep-amount" required>
                    </div>
                    <div class="input-group">
                        <label>Transaction ID (TRX ID Reference)</label>
                        <input type="text" placeholder="Enter 11-digit Transaction ID" required>
                    </div>
                    <button class="form-action-btn" type="submit">Submit Deposit Request</button>
                </form>
            </div>

            <!-- Withdrawal Interface -->
            <div class="op-card">
                <h3>📤 Secure Vault Exit (Withdrawal)</h3>
                <form id="withdraw-form" onsubmit="handleWithdrawal(event)">
                    <div class="input-group">
                        <label>Destination Account Number</label>
                        <input type="text" placeholder="03XXXXXXXXX" required>
                    </div>
                    <div class="input-group">
                        <label>Exit Amount (PKR)</label>
                        <input type="number" min="100" placeholder="Minimum Rs. 100" id="wit-amount" required>
                    </div>
                    <small style="color: var(--promo-red); display:block; margin-bottom:15px; font-size:11.5px; font-weight: 500;">
                        * Note: 10% Safe Operational Tax will be cut automatically from this transit.
                    </small>
                    <button class="form-action-btn" style="background: var(--gold-warning); color: #0a0e1a; box-shadow: 0 4px 12px rgba(245, 158, 11, 0.2);" type="submit">Initialize Liquidity Exit</button>
                </form>
            </div>
        </div>

        <!-- 4. Dynamic Cloud Computing Node Matrix Grid -->
        <div class="section-title">Available Cloud Mining Arrays</div>
        <div id="nodes-display-grid"></div>
    </div>

    <!-- 5. Firebase Dynamic JavaScript Logic Module -->
    <script type="module">
        import { initializeApp } from "https://unpkg.com/firebase@10.8.0/firebase-app.js";
        import { getDatabase, ref, set, get, update, onValue } from "https://unpkg.com/firebase@10.8.0/firebase-database.js";
        import { getAuth, onAuthStateChanged, signOut } from "https://unpkg.com/firebase@10.8.0/firebase-auth.js";

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
        const database = getDatabase(app);
        const auth = getAuth(app);

        let currentUserId = null;

        const pakTradeNodes = [
            { id: "p_a1", name: "Pod Alpha-1", cost: 200, dailyYield: 15, days: 30, img: "https://images.unsplash.com/photo-1639762681485-074b7f938ba0?w=400&q=80", cat: "normal" },
            { id: "p_a2", name: "Pod Alpha-2", cost: 400, dailyYield: 30, days: 30, img: "https://images.unsplash.com/photo-1558494949-ef010cbdcc31?w=400&q=80", cat: "normal" },
            { id: "p_a3", name: "Pod Alpha-3", cost: 600, dailyYield: 45, days: 30, img: "https://images.unsplash.com/photo-1563770660941-20978e870e26?w=400&q=80", cat: "normal" },
            { id: "r_s1", name: "Rig Stratum-1 [PROMO]", cost: 3000, dailyYield: 300, days: 10, img: "https://images.unsplash.com/photo-1640340434855-6084b1f4901c?w=400&q=80", cat: "special" },
            { id: "r_s2", name: "Rig Stratum-2 [PROMO]", cost: 4000, dailyYield: 360, days: 12, img: "https://images.unsplash.com/photo-1624996379697-f01d168b1a52?w=400&q=80", cat: "special" },
            { id: "r_s3", name: "Rig Stratum-3 [PROMO]", cost: 5000, dailyYield: 420, days: 15, img: "https://images.unsplash.com/photo-1544383835-bda2bc66a55d + ?w=400&q=80", cat: "special" },
            { id: "m_qc", name: "Matrix Quantum-Core", cost: 100000, dailyYield: 8500, days: 45, img: "https://images.unsplash.com/photo-1607604276583-eef5d076aa5f?w=400&q=80", cat: "exclusive" }
        ];

        // 1. Auth Observer Interface Tracking Loop
        onAuthStateChanged(auth, (user) => {
            if (user) {
                currentUserId = user.uid;
                listenToUserWallet(currentUserId);
            } else {
                currentUserId = null;
                document.getElementById('user-balance').innerText = `Rs. 0`;
                document.getElementById('user-referrals').innerText = `Rs. 0`;
                document.getElementById('active-nodes-count').innerText = "0";
            }
        });

        function listenToUserWallet(uid) {
            const walletRef = ref(database, 'users/' + uid);
            onValue(walletRef, (snapshot) => {
                const data = snapshot.val();
                if (data) {
                    document.getElementById('user-balance').innerText = `Rs. ${data.balance.toLocaleString()}`;
                    document.getElementById('user-referrals').innerText = `Rs. ${data.referralEarnings.toLocaleString()}`;
                    document.getElementById('active-nodes-count').innerText = data.leasedCount;
                    window.currentUserWallet = data;
                } else {
                    const defaultWallet = { balance: 1000, referralEarnings: 0, leasedCount: 0, email: auth.currentUser.email };
                    set(walletRef, defaultWallet);
                }
            });
        }

        // Global Operations Hooks Connected to Layout UI Buttons
        window.handleDeposit = function(e) {
            e.preventDefault();
            if (!currentUserId) return alert("Please login first, sweetie!");
            const amt = parseInt(document.getElementById('dep-amount').value);
            const walletRef = ref(database, 'users/' + currentUserId);
            const newBalance = (window.currentUserWallet?.balance || 0) + amt;
            update(walletRef, { balance: newBalance }).then(() => {
                alert(`Gateway Success!\nRs. ${amt} has been securely wired into your Cloud Wallet.`);
                e.target.reset();
            });
        };

        window.handleWithdrawal = function(e) {
            e.preventDefault();
            if (!currentUserId) return alert("Please login first!");
            const amt = parseInt(document.getElementById('wit-amount').value);
            const currentBal = window.currentUserWallet?.balance || 0;
            if (amt > currentBal) return alert("Error: Insufficient Vault Funds.");
            const walletRef = ref(database, 'users/' + currentUserId);
            const newBalance = currentBal - amt;
            update(walletRef, { balance: newBalance }).then(() => {
                alert(`Withdrawal Registered!\nNet Paid (After 10% Tax): Rs. ${amt * 0.90}`);
                e.target.reset();
            });
        };

        window.leaseProcessor = function(id, cost) {
            if (!currentUserId) return alert("Please login first!");
            const currentBal = window.currentUserWallet?.balance || 0;
            if (currentBal < cost) return alert(`Insufficient Balance!\nRequired: Rs. ${cost}`);
            const walletRef = ref(database, 'users/' + currentUserId);
            update(walletRef, {
                balance: currentBal - cost,
                leasedCount: (window.currentUserWallet?.leasedCount || 0) + 1,
                referralEarnings: (window.currentUserWallet?.referralEarnings || 0) + (cost * 0.10)
            }).then(() => alert("Node engine deployed successfully!"));
        };

        window.logoutUser = function() {
            signOut(auth).then(() => alert("Logged out safely, sweetie!"));
        };

        // Static Secondary Helpers Render Module
        function renderPakTradeStore() {
            const gridTarget = document.getElementById('nodes-display-grid');
            gridTarget.innerHTML = ''; 
            pakTradeNodes.forEach((node) => {
                const isSpecial = node.cat === "special";
                const badgeColor = isSpecial ? "var(--promo-red)" : "var(--neon-green)";
                gridTarget.innerHTML += `
                    <div class="node-premium-card ${isSpecial ? 'promo-active-border' : ''}">
                        <div class="node-image-wrap">
                            ${isSpecial ? `<span class="promo-ribbon">HOT Promo</span>` : ''}
                            <img src="${node.img}" alt="${node.name}">
                            <span class="node-badge-cost" style="background: ${badgeColor};">Rs. ${node.cost.toLocaleString()}</span>
                        </div>
                        <div class="node-meta-body">
                            <h3>${node.name}</h3>
                            <div class="meta-row"><span>Daily Payout:</span><b style="color: ${badgeColor};">Rs. ${node.dailyYield}</b></div>
                            <div class="meta-row"><span>Total Net:</span><b>Rs. ${node.dailyYield * node.days}</b></div>
                            <div class="meta-row"><span>Cycle:</span><span>${node.days} Days Contract</span></div>
                            <div class="timer-box"><span class="timer-icon">${isSpecial ? '🔥' : '⚡'}</span><p class="realtime-clock-node">24:00:00</p></div>
                            <button class="node-action-btn" style="${isSpecial ? 'border-color: var(--promo-red); color: var(--promo-red);' : ''}" onclick="leaseProcessor('${node.id}', ${node.cost})">Lease Node Engine</button>
                        </div>
                    </div>`;
            });
        }

        window.onload = function() {
            renderPakTradeStore();
            setInterval(() => {
                const now = new Date();
                const timeString = `${(23 - now.getHours()).toString().padStart(2,'0')}:${(59 - now.getMinutes()).toString().padStart(2,'0')}:${(59 - now.getSeconds()).toString().padStart(2,'0')}`;
                document.querySelectorAll('.realtime-clock-node').forEach(c => c.innerText = timeString);
            }, 1000);
            
            // Build Quick Simulated Ledger Ticker Track
            const entries = ['0301***412 withdrew Rs. 3,500', '0345***992 deployed Pod Alpha-2', '0321***104 claimed Level-1 Reward'];
            document.getElementById('payout-ticker').innerHTML = entries.map(e => `• [SYSTEM DATA LOG] User ${e} &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`).join('');
        };
    </script>
</body>
</html>
