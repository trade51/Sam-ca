<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pak Trade | Professional Dashboard</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: 'Segoe UI', sans-serif; background-color: #0a0e14; color: #ffffff; display: flex; min-height: 100vh; }
        
        /* Sidebar Styling */
        .sidebar { width: 250px; background: #111827; padding: 20px; border-right: 1px solid #1f2937; }
        .logo { font-size: 1.8rem; font-weight: bold; color: #3b82f6; margin-bottom: 30px; }
        .sidebar li { padding: 15px; cursor: pointer; list-style: none; border-bottom: 1px solid #1f2937; transition: 0.3s; }
        .sidebar li:hover { color: #3b82f6; }

        /* Main Content */
        .main-content { flex: 1; padding: 40px; }
        .card { background: #111827; padding: 20px; border-radius: 10px; border: 1px solid #374151; margin-bottom: 20px; }
        
        /* Stats Styling */
        .stats-cards { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; margin-bottom: 20px; }
        .stats-cards p { font-size: 1.5rem; font-weight: bold; color: #3b82f6; margin-top: 10px; }
        
        /* Form Styling */
        input { padding: 12px; width: 250px; background: #0a0e14; border: 1px solid #374151; color: white; border-radius: 5px; }
        button { padding: 12px 25px; background: #3b82f6; border: none; color: white; cursor: pointer; border-radius: 5px; font-weight: bold; }
        
        /* Responsive Fix */
        @media (max-width: 768px) { body { flex-direction: column; } .sidebar { width: 100%; } }
    </style>
</head>
<body>

    <div class="sidebar">
        <div class="logo">Pak Trade</div>
        <ul>
            <li>Dashboard</li>
            <li>Market Data</li>
            <li>Settings</li>
            <li id="logoutBtn" style="color: #ef4444;">Logout</li>
        </ul>
    </div>

    <div class="main-content">
        <div class="card" style="border: 1px solid #3b82f6;">
            <h3>How Pak Trade Works</h3>
            <div style="display: flex; justify-content: space-around; margin-top: 15px; text-align: center;">
                <div>💳<p style="font-size: 0.7rem; color:white;">1. Deposit</p></div>
                <div>📈<p style="font-size: 0.7rem; color:white;">2. Trade</p></div>
                <div>💰<p style="font-size: 0.7rem; color:white;">3. Earn</p></div>
                <div>🏦<p style="font-size: 0.7rem; color:white;">4. Withdraw</p></div>
            </div>
        </div>

        <div class="stats-cards">
            <div class="card"><h3>Total Balance</h3><p id="userBalance">$0.00</p></div>
            <div class="card"><h3>Active Trades</h3><p style="color:#10b981;">0</p></div>
            <div class="card"><h3>Security Status</h3><p style="font-size: 1rem; margin-top: 15px;">SSL Encrypted</p></div>
        </div>

        <div class="card">
            <h3>Add Funds to Account</h3>
            <div style="margin-top: 15px;">
                <input type="number" id="depositAmount" placeholder="Amount (USD)">
                <button id="submitDeposit">Submit Request</button>
            </div>
        </div>
    </div>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/9.6.1/firebase-app.js";
        import { getAuth, signOut, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/9.6.1/firebase-auth.js";
        import { getDatabase, ref, onValue, push } from "https://www.gstatic.com/firebasejs/9.6.1/firebase-database.js";

        // Apna Firebase Config yahan paste karein
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
        const auth = getAuth(app);
        const db = getDatabase(app);

        // User Status Check
        onAuthStateChanged(auth, (user) => {
            if (user) {
                onValue(ref(db, 'users/' + user.uid + '/balance'), (snap) => {
                    document.getElementById('userBalance').innerText = snap.val() ? `$${snap.val()}` : "$0.00";
                });
            } else { window.location.href = "login.html"; }
        });

        // Deposit Logic
        document.getElementById('submitDeposit').onclick = () => {
            const amt = document.getElementById('depositAmount').value;
            if(amt > 0) {
                push(ref(db, 'deposit_requests/'), { userId: auth.currentUser.uid, amount: amt, status: 'pending' })
                .then(() => alert("Request sent successfully, sweetie!"));
            }
        };

        // Logout Logic
        document.getElementById('logoutBtn').onclick = () => signOut(auth).then(() => location.href = "login.html");
    </script>
</body>
</html>
