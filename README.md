<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pak Trade Global LLC - Node Cloud Network</title>
    <style>
        /* Base Architecture Setup */
        body {
            background-color: #0b0f19;
            color: #e2e8f0;
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            margin: 0;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        h1 {
            text-align: center;
            color: #fff;
            margin-bottom: 10px;
            font-weight: 800;
        }

        .subtitle {
            text-align: center;
            color: #8492a6;
            font-size: 14px;
            margin-bottom: 40px;
        }

        /* Responsive Grid System */
        #nodes-display-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 25px;
            padding: 15px 0;
        }

        /* Glassmorphism Premium Node Card */
        .node-premium-card {
            background: rgba(255, 255, 255, 0.02);
            border: 1px solid rgba(255, 255, 255, 0.06);
            border-radius: 20px;
            overflow: hidden;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .node-premium-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.5), 0 0 15px rgba(0, 230, 118, 0.1);
            border-color: rgba(0, 230, 118, 0.2);
        }

        /* Special Promo Border Activation */
        .promo-active-border {
            border: 1px solid rgba(255, 62, 62, 0.2) !important;
            background: linear-gradient(145deg, rgba(255, 62, 62, 0.02) 0%, rgba(255,255,255,0.01) 100%);
        }

        .promo-active-border:hover {
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.6), 0 0 15px rgba(255, 62, 62, 0.15) !important;
            border-color: rgba(255, 62, 62, 0.4) !important;
        }

        /* Image Containment Design */
        .node-image-wrap {
            position: relative;
            width: 100%;
            height: 160px;
            overflow: hidden;
        }

        .node-image-wrap img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            filter: brightness(0.85) contrast(1.1);
        }

        .node-badge-cost {
            position: absolute;
            bottom: 12px;
            right: 12px;
            color: #0b0f19;
            font-weight: 800;
            padding: 6px 12px;
            border-radius: 10px;
            font-size: 13px;
        }

        /* Hot Offer Ribbon badge */
        .promo-ribbon {
            position: absolute;
            top: 10px;
            left: 10px;
            background: #ff3e3e;
            color: #fff;
            font-size: 9px;
            font-weight: 900;
            padding: 4px 8px;
            border-radius: 6px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            z-index: 2;
            box-shadow: 0 2px 5px rgba(0,0,0,0.3);
        }

        /* Metadata Parameters Styling */
        .node-meta-body {
            padding: 20px;
        }

        .node-meta-body h3 {
            margin: 0 0 15px 0;
            font-size: 18px;
            font-weight: 700;
            color: #fff;
        }

        .meta-row {
            display: flex;
            justify-content: space-between;
            font-size: 13px;
            color: #8492a6;
            margin-bottom: 10px;
        }

        .cycle-tag {
            background: rgba(255,255,255,0.05);
            color: #e2e8f0;
            padding: 2px 8px;
            border-radius: 6px;
            font-size: 11px;
        }

        /* Realtime Distribution Clock Block */
        .timer-box {
            display: flex;
            align-items: center;
            gap: 10px;
            background: rgba(0, 0, 0, 0.2);
            border: 1px solid rgba(255,255,255,0.03);
            padding: 10px;
            border-radius: 12px;
            margin: 18px 0 15px 0;
        }

        .timer-icon {
            font-size: 16px;
        }

        .timer-text-wrap small {
            display: block;
            font-size: 10px;
            color: #64748b;
            text-transform: uppercase;
        }

        .timer-text-wrap p {
            margin: 2px 0 0 0;
            font-size: 14px;
            font-weight: 700;
            color: #f59e0b;
            font-family: monospace;
        }

        /* Interactive Action Elements */
        .node-action-btn {
            width: 100%;
            background: transparent;
            border: 1px solid rgba(0,230,118,0.3);
            color: #00e676;
            padding: 12px;
            border-radius: 12px;
            font-weight: 700;
            font-size: 13px;
            cursor: pointer;
            transition: 0.2s;
        }

        .node-action-btn:hover {
            background: #00e676;
            color: #0b0f19;
            box-shadow: 0 5px 15px rgba(0,230,118,0.2);
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Pak Trade Infrastructure Nodes</h1>
        <p class="subtitle">Select and lease an optimized cloud server array to initiate distributed data cycles.</p>
        
        <!-- Target Grid for JavaScript Injection Loop -->
        <div id="nodes-display-grid"></div>
    </div>

    <script>
        // System Master Node Dataset (21 Nodes Array)
        const pakTradeNodes = [
            // --- NORMAL PODS (30 Days Standard Cycle) ---
            { id: "p_a1", name: "Pod Alpha-1", cost: 200, dailyYield: 15, days: 30, img: "https://images.unsplash.com/photo-1639762681485-074b7f938ba0?w=400&q=80", cat: "normal" },
            { id: "p_a2", name: "Pod Alpha-2", cost: 400, dailyYield: 30, days: 30, img: "https://images.unsplash.com/photo-1558494949-ef010cbdcc31?w=400&q=80", cat: "normal" },
            { id: "p_a3", name: "Pod Alpha-3", cost: 600, dailyYield: 45, days: 30, img: "https://images.unsplash.com/photo-1563770660941-20978e870e26?w=400&q=80", cat: "normal" },
            { id: "p_a4", name: "Pod Alpha-4", cost: 800, dailyYield: 60, days: 30, img: "https://images.unsplash.com/photo-1600132806370-bf17e65e942f?w=400&q=80", cat: "normal" },
            { id: "p_a5", name: "Pod Alpha-5", cost: 1000, dailyYield: 75, days: 30, img: "https://images.unsplash.com/photo-1518770660439-4636190af475?w=400&q=80", cat: "normal" },
            { id: "p_a6", name: "Pod Alpha-6", cost: 1500, dailyYield: 112, days: 30, img: "https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?w=400&q=80", cat: "normal" },
            { id: "p_a7", name: "Pod Alpha-7", cost: 2000, dailyYield: 150, days: 30, img: "https://images.unsplash.com/photo-1621761191319-c6fb62004040?w=400&q=80", cat: "normal" },
            
            // --- 5 SPECIAL MINING MACHINE OFFERS (10-20 Days Short-Term Cycles) ---
            { id: "r_s1", name: "Rig Stratum-1 [PROMO]", cost: 3000, dailyYield: 300, days: 10, img: "https://images.unsplash.com/photo-1640340434855-6084b1f4901c?w=400&q=80", cat: "special" },
            { id: "r_s2", name: "Rig Stratum-2 [PROMO]", cost: 4000, dailyYield: 360, days: 12, img: "https://images.unsplash.com/photo-1624996379697-f01d168b1a52?w=400&q=80", cat: "special" },
            { id: "r_s3", name: "Rig Stratum-3 [PROMO]", cost: 5000, dailyYield: 420, days: 15, img: "https://images.unsplash.com/photo-1544383835-bda2bc66a55d?w=400&q=80", cat: "special" },
            { id: "r_s4", name: "Rig Stratum-4 [PROMO]", cost: 7000, dailyYield: 560, days: 18, img: "https://images.unsplash.com/photo-1601597111158-2fceff292cdc?w=400&q=80", cat: "special" },
            { id: "r_s5", name: "Rig Stratum-5 [PROMO]", cost: 10000, dailyYield: 750, days: 20, img: "https://images.unsplash.com/photo-1581092160607-ee22621dd758?w=400&q=80", cat: "special" },
            
            // --- HIGH-TIER ENTERPRISE OPERATIONS (45 Days Cycle) ---
            { id: "r_s6", name: "Rig Stratum-6", cost: 15000, dailyYield: 1125, days: 45, img: "https://images.unsplash.com/photo-1468495244123-6c6c332eeece?w=400&q=80", cat: "exclusive" },
            { id: "r_s7", name: "Rig Stratum-7", cost: 20000, dailyYield: 1500, days: 45, img: "https://images.unsplash.com/photo-1516321318423-f06f85e504b3?w=400&q=80", cat: "exclusive" },
            { id: "m_o1", name: "Matrix Overdrive-1", cost: 30000, dailyYield: 2400, days: 45, img: "https://images.unsplash.com/photo-1639322537228-f710d846310a?w=400&q=80", cat: "exclusive" },
            { id: "m_o2", name: "Matrix Overdrive-2", cost: 40000, dailyYield: 3200, days: 45, img: "https://images.unsplash.com/photo-1614064641938-3bbee52942c7?w=400&q=80", cat: "exclusive" },
            { id: "m_o3", name: "Matrix Overdrive-3", cost: 50000, dailyYield: 4000, days: 45, img: "https://images.unsplash.com/photo-1631553127988-347f8976b3f7?w=400&q=80", cat: "exclusive" },
            { id: "m_o4", name: "Matrix Overdrive-4", cost: 60000, dailyYield: 4800, days: 45, img: "https://images.unsplash.com/photo-1504384308090-c894fdcc538d?w=400&q=80", cat: "exclusive" },
            { id: "m_o5", name: "Matrix Overdrive-5", cost: 70000, dailyYield: 5600, days: 45, img: "https://images.unsplash.com/photo-1550751827-4bd374c3f58b?w=400&q=80", cat: "exclusive" },
            { id: "m_o6", name: "Matrix Overdrive-6", cost: 85000, dailyYield: 6800, days: 45, img: "https://images.unsplash.com/photo-1451187580459-43490279c0fa?w=400&q=80", cat: "exclusive" },
            { id: "m_qc", name: "Matrix Quantum-Core", cost: 100000, dailyYield: 8500, days: 45, img: "https://images.unsplash.com/photo-1607604276583-eef5d076aa5f?w=400&q=80", cat: "exclusive" }
        ];

        // Dynamic Card Interface Generation Module
        function renderPakTradeStore() {
            const gridTarget = document.getElementById('nodes-display-grid');
            gridTarget.innerHTML = ''; 

            pakTradeNodes.forEach((node) => {
                const totalProfit = node.dailyYield * node.days;
                const isSpecial = node.cat === "special";
                
                // Color configuration mapping logic based on type rules
                const badgeColor = isSpecial ? "#ff3e3e" : "#00e676";
                const textShadow = isSpecial ? "0 4px 10px rgba(255, 62, 62, 0.4)" : "0 4px 10px rgba(0, 230, 118, 0.4)";
                
                const cardHtml = `
                    <div class="node-premium-card ${isSpecial ? 'promo-active-border' : ''}">
                        <div class="node-image-wrap">
                            ${isSpecial ? `<span class="promo-ribbon">HOT OFFER</span>` : ''}
                            <img src="${node.img}" alt="${node.name}" loading="lazy">
                            <span class="node-badge-cost" style="background: ${badgeColor}; box-shadow: ${textShadow};">
                                Rs. ${node.cost.toLocaleString()}
                            </span>
                        </div>
                        
                        <div class="node-meta-body">
                            <h3>${node.name}</h3>
                            <div class="meta-row">
                                <span>Daily Yield:</span>
                                <b style="color: ${badgeColor}; font-weight:700;">Rs. ${node.dailyYield.toLocaleString()}</b>
                            </div>
                            <div class="meta-row">
                                <span>Total Income:</span>
                                <b style="color: #fff;">Rs. ${totalProfit.toLocaleString()}</b>
                            </div>
                            <div class="meta-row">
                                <span>Contract Cycle:</span>
                                <span class="cycle-tag" style="${isSpecial ? 'color: #ff3e3e; background: rgba(255,62,62,0.1);' : ''}">
                                    ${node.days} Days Block
                                </span>
                            </div>
                            
                            <div class="timer-box">
                                <span class="timer-icon">${isSpecial ? '🔥' : '⚡'}</span>
                                <div class="timer-text-wrap">
                                    <small>${isSpecial ? 'Promo Loop Sync' : 'Next Distribution Loop'}</small>
                                    <p class="realtime-clock-node">24:00:00</p>
                                </div>
                            </div>
                            
                            <button class="node-action-btn" style="${isSpecial ? 'border-color: #ff3e3e; color: #ff3e3e;' : ''}" 
                                    onclick="initializeLeaseNode('${node.id}', ${node.cost})">
                                ${isSpecial ? 'Lease Special Node' : 'Lease Computing Node'}
                            </button>
                        </div>
                    </div>
                `;
                gridTarget.innerHTML += cardHtml;
            });
            
            initializeSystemGlobalClocks();
        }

        // Live Countdown Loops Logic Engine
        function initializeSystemGlobalClocks() {
            setInterval(() => {
                const clocks = document.querySelectorAll('.realtime-clock-node');
                const now = new Date();
                const hrs = 23 - now.getHours();
                const mins = 59 - now.getMinutes();
                const secs = 59 - now.getSeconds();

                const timeString = 
                    `${hrs.toString().padStart(2, '0')}:${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`;

                clocks.forEach(clock => {
                    clock.innerText = timeString;
                });
            }, 1000);
        }

        // Interactive Lease Trigger Action Function
        function initializeLeaseNode(nodeId, nodeCost) {
            console.log(`Lease request initialized for node: ${nodeId} with price Rs.${nodeCost}`);
            alert(`Node Request Processing!\nTarget Node ID: ${nodeId}\nRequired Balance: Rs. ${nodeCost}`);
            // Firebase balance modification logic or admin log stream can be attached here
        }

        // Auto Execute Render Engine on page init
        window.onload = renderPakTradeStore;
    </script>
</body>
</html>
