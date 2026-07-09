<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pak Trade Pro | Premium Terminal</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap');
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Inter', sans-serif; }
        body { background: radial-gradient(circle at top right, #0f172a, #020617); color: #ffffff; min-height: 100vh; display: flex; }
        
        .sidebar { width: 260px; background: rgba(17, 24, 39, 0.7); backdrop-filter: blur(20px); border-right: 1px solid rgba(255,255,255,0.1); padding: 30px; position: fixed; height: 100%; }
        .main-content { margin-left: 260px; flex: 1; padding: 40px; }
        .card { background: rgba(30, 41, 59, 0.5); backdrop-filter: blur(15px); border: 1px solid rgba(255,255,255,0.1); padding: 25px; border-radius: 20px; box-shadow: 0 8px 32px rgba(0,0,0,0.3); transition: 0.3s; }
        
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 25px; margin-top: 25px; }
        .btn-glow { background: linear-gradient(135deg, #3b82f6, #1d4ed8); border: none; padding: 12px 25px; border-radius: 12px; color: white; cursor: pointer; box-shadow: 0 0 15px rgba(59, 130, 246, 0.4); font-weight: 600; width: 100%; margin-top: 10px; }
        .node-img { width: 100%; height: 140px; object-fit: cover; border-radius: 15px; margin-bottom: 15px; }
        .toast { position: fixed; bottom: 20px; right: 20px; background: #1f2937; padding: 15px; border-left: 4px solid #3b82f6; border-radius: 5px; display: none; }
    </style>
</head>
<body>

    <div class="sidebar">
        <h2 style="margin-bottom: 40px; letter-spacing: -1px;">PAK<span style="color:#3b82f6;">TRADE</span></h2>
        <ul style="list-style:none;">
            <li style="margin-bottom:20px; color:#3b82f6; font-weight:bold;">Dashboard</li>
            <li style="margin-bottom:20px; opacity:0.7;">Mining Nodes</li>
            <li style="margin-bottom:20px; opacity:0.7;">History</li>
            <li id="logoutBtn" style="color:#ef4444; cursor:pointer; margin-top:50px;">Logout</li>
        </ul>
    </div>

    <div class="main-content">
        <div style="display:flex; justify-content:space-between; align-items:center;">
            <h1>Terminal</h1>
            <div class="card" style="padding:15px 30px;">Balance: <span id="userBalance" style="color:#10b981; font-weight:bold;">$0.00</span></div>
        </div>

        <div class="grid">
            <div class="card"><h3>Deposit</h3><input type="number" id="depAmt" style="width:100%; padding:10px; margin:10px 0; background:transparent; border:1px solid #475569; border-radius:8px; color:white;"><button class="btn-glow" id="subDep">Submit Request</button></div>
            <div class="card"><h3>Withdraw</h3><input type="number" id="witAmt" style="width:100%; padding:10px; margin:10px 0; background:transparent; border:1px solid #475569; border-radius:8px; color:white;"><button class="btn-glow" style="background:#059669;" id="subWit">Request Profit</button></div>
            <div class="card"><h3>Referral</h3><p style="margin:10px 0;">Earn 10% on every invite!</p><button class="btn-glow" style="background:#f59e0b;">Copy Link</button></div>
        </div>

        <h3 style="margin-top:40px;">Active Mining Nodes (20+)</h3>
        <div class="grid" id="nodesContainer"></div>
    </div>

    <div id="toast" class="toast">New Mining Activity Detected!</div>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/9.6.1/firebase-app.js";
        import { getAuth, signOut } from "https://www.gstatic.com/firebasejs/9.6.1/firebase-auth.js";
        import { getDatabase, ref, onValue, push } from "https://www.gstatic.com/firebasejs/9.6.1/firebase-database.js";

        const firebaseConfig = { /* Apna config daal dena */ };
        const app = initializeApp(firebaseConfig);
        const auth = getAuth(app);
        const db = getDatabase(app);

        // Load 20 Nodes
        const container = document.getElementById('nodesContainer');
        for (let i = 1; i <= 20; i++) {
            container.innerHTML += `
                <div class="card">
                    <img src="https://images.unsplash.com/photo-1622737133649-6238383a6401?w=400" class="node-img">
                    <h3>Mining Node v${i}</h3>
                    <p style="color:#94a3b8; margin:5px 0;">Daily Profit: $${i * 2}</p>
                    <button class="btn-glow" onclick="alert('Node ${i} Started!')">Activate</button>
                </div>
            `;
        }

        // Live Notification Toast
        setInterval(() => {
            const toast = document.getElementById('toast');
            toast.style.display = 'block';
            setTimeout(() => toast.style.display = 'none', 3000);
        }, 15000);

        document.getElementById('logoutBtn').onclick = () => signOut(auth).then(() => location.href = "login.html");
    </script>
</body>
</html>
