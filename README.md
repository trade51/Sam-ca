<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SAM Events & Production - Casting Registration</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #121212;
            color: #ffffff;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
            flex-direction: column;
        }

        /* Container Styling */
        .container {
            background: #1a1a1a;
            border: 2px solid #d4af37; /* Gold Border */
            border-radius: 12px;
            padding: 30px;
            width: 100%;
            max-width: 600px;
            box-shadow: 0px 8px 24px rgba(212, 175, 55, 0.2);
            position: relative;
        }

        /* Eagle Eye Trigger Element */
        .logo-area {
            text-align: center;
            margin-bottom: 25px;
            cursor: pointer; /* Change cursor to pointer for double click */
            user-select: none;
        }

        .logo-area h2 {
            color: #d4af37;
            font-size: 24px;
            letter-spacing: 2px;
        }

        .logo-area p {
            color: #aaaaaa;
            font-size: 12px;
            text-transform: uppercase;
            margin-top: 5px;
        }

        h3 {
            text-align: center;
            color: #ffffff;
            font-size: 20px;
            margin-bottom: 5px;
        }

        .subtitle {
            text-align: center;
            color: #888888;
            font-size: 14px;
            margin-bottom: 25px;
        }

        /* Form Fields */
        .input-group {
            margin-bottom: 20px;
        }

        .input-row {
            display: flex;
            gap: 15px;
        }

        .input-row .input-group {
            flex: 1;
        }

        label {
            display: block;
            color: #d4af37;
            font-size: 14px;
            margin-bottom: 8px;
            font-weight: 600;
        }

        input[type="text"],
        input[type="number"],
        input[type="tel"],
        select,
        input[type="file"] {
            width: 100%;
            padding: 12px;
            background: #2a2a2a;
            border: 1px solid #444444;
            border-radius: 6px;
            color: #ffffff;
            font-size: 15px;
            transition: all 0.3s ease;
        }

        input:focus, select:focus {
            outline: none;
            border-color: #d4af37;
            background: #333333;
        }

        .submit-btn {
            width: 100%;
            padding: 14px;
            background: linear-gradient(45deg, #d4af37, #aa7c11);
            border: none;
            border-radius: 6px;
            color: #000000;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.2s ease, opacity 0.2s ease;
            margin-bottom: 15px;
        }

        .submit-btn:hover {
            opacity: 0.9;
            transform: translateY(-2px);
        }

        /* Toggle Button */
        .toggle-btn {
            background: transparent;
            border: 1px solid #d4af37;
            color: #d4af37;
            padding: 8px 16px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 13px;
            display: block;
            margin: 20px auto 0 auto;
            transition: all 0.3s ease;
        }

        .toggle-btn:hover {
            background: #d4af37;
            color: #000000;
        }

        /* Filter Controls */
        .filter-controls {
            margin-bottom: 15px;
            display: flex;
            gap: 10px;
        }

        .filter-controls input, .filter-controls select {
            padding: 8px;
            background: #2a2a2a;
            border: 1px solid #444444;
            color: #fff;
            border-radius: 4px;
            font-size: 14px;
            flex: 1;
        }

        /* Admin Table View */
        .hidden {
            display: none !important;
        }

        .table-wrapper {
            overflow-x: auto;
            margin-top: 20px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
            color: #ffffff;
        }

        th, td {
            padding: 12px;
            text-align: left;
            border-bottom: 1px solid #333333;
        }

        th {
            background-color: #2a2a2a;
            color: #d4af37;
        }

        .preview-img {
            width: 50px;
            height: 50px;
            object-fit: cover;
            border-radius: 4px;
            border: 1px solid #d4af37;
        }

        .badge {
            background: #d4af37;
            color: #000;
            padding: 2px 8px;
            border-radius: 12px;
            font-size: 12px;
            text-transform: capitalize;
            font-weight: bold;
        }

        .whatsapp-link {
            background: #25D366;
            color: white;
            padding: 5px 10px;
            text-decoration: none;
            border-radius: 4px;
            font-size: 12px;
            font-weight: bold;
            display: inline-block;
        }

        .whatsapp-link:hover {
            background: #1ebd59;
        }
    </style>

    <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-database-compat.js"></script>
</head>
<body>

    <div class="container" id="formSection">
        <div class="logo-area" ondblclick="triggerEagleEye()">
            <h2>SAM EVENTS & PRODUCTION</h2>
            <p>Committed With Quality</p>
        </div>
        
        <h3>Casting Call Registration</h3>
        <p class="subtitle">Enter your details to apply for upcoming projects</p>

        <form id="castingForm">
            <div class="input-group">
                <label for="fullName">Full Name</label>
                <input type="text" id="fullName" placeholder="Enter your full name" required>
            </div>

            <div class="input-row">
                <div class="input-group">
                    <label for="age">Age</label>
                    <input type="number" id="age" placeholder="Age" required>
                </div>
                <div class="input-group">
                    <label for="category">Category</label>
                    <select id="category" required>
                        <option value="" disabled selected>Select Category</option>
                        <option value="girls">Girl</option>
                        <option value="boys">Boy</option>
                        <option value="children">Child</option>
                        <option value="uncles">Uncle</option>
                        <option value="aunties">Auntie</option>
                    </select>
                </div>
            </div>

            <div class="input-group">
                <label for="phone">WhatsApp Number</label>
                <input type="tel" id="phone" placeholder="e.g. 03175052697" required>
            </div>

            <div class="input-group">
                <label for="photo">Upload Photo</label>
                <input type="file" id="photo" accept="image/*" required>
            </div>

            <button type="submit" class="submit-btn" id="submitBtn">Submit Application</button>
        </form>
    </div>

    <div class="container hidden" id="adminSection">
        <div class="logo-area">
            <h2>SAM EVENTS - EAGLE EYE</h2>
            <p>Review Registered Talent (Realtime Database)</p>
        </div>

        <h3>Received Applications</h3>

        <div class="filter-controls">
            <input type="text" id="searchName" placeholder="Search by name..." oninput="filterData()">
            <select id="filterCategory" onchange="filterData()">
                <option value="all">All Categories</option>
                <option value="girls">Girls</option>
                <option value="boys">Boys</option>
                <option value="children">Children</option>
                <option value="uncles">Uncles</option>
                <option value="aunties">Aunties</option>
            </select>
        </div>
        
        <div class="table-wrapper">
            <table>
                <thead>
                    <tr>
                        <th>Photo</th>
                        <th>Name</th>
                        <th>Age</th>
                        <th>Category</th>
                        <th>Action</th>
                    </tr>
                </thead>
                <tbody id="adminTableBody">
                    <tr><td colspan="5" style="text-align: center; color: #888;">Connecting to Firebase...</td></tr>
                </tbody>
            </table>
        </div>

        <button class="toggle-btn" onclick="toggleView('form')">Back to Registration Form</button>
    </div>

    <script>
        // 1. Initialize Firebase
        const firebaseConfig = {
            apiKey: "AIzaSyBqtvNJW_HNv4H2EAzeAhNL-tiUjX1huEg",
            authDomain: "trade51-f64d5.firebaseapp.com",
            databaseURL: "https://trade51-f64d5-default-rtdb.firebaseio.com",
            projectId: "trade51-f64d5",
            storageBucket: "trade51-f64d5.firebasestorage.app",
            messagingSenderId: "38759095579",
            appId: "1:38759095579:web:013d72ab4b5183f99347be"
        };

        firebase.initializeApp(firebaseConfig);
        const database = firebase.database();
        let allSubmissions = []; // Global variable to hold fetched firebase data

        // 2. Form Submission to Firebase
        document.getElementById('castingForm').addEventListener('submit', function(e) {
            e.preventDefault();

            const submitBtn = document.getElementById('submitBtn');
            submitBtn.innerText = "Submitting...";
            submitBtn.disabled = true;

            const fullName = document.getElementById('fullName').value;
            const age = document.getElementById('age').value;
            const category = document.getElementById('category').value;
            const phone = document.getElementById('phone').value;
            const photoInput = document.getElementById('photo');

            const file = photoInput.files[0];
            const reader = new FileReader();

            reader.onloadend = function() {
                const newAuditionRef = database.ref('auditions').push();
                
                newAuditionRef.set({
                    name: fullName,
                    age: age,
                    category: category,
                    phone: phone,
                    photo: reader.result 
                }).then(() => {
                    alert('Application successfully sent, sweetie!');
                    document.getElementById('castingForm').reset();
                    submitBtn.innerText = "Submit Application";
                    submitBtn.disabled = false;
                }).catch((error) => {
                    alert('Database Error: ' + error.message);
                    submitBtn.innerText = "Submit Application";
                    submitBtn.disabled = false;
                });
            }

            if (file) {
                reader.readAsDataURL(file);
            }
        });

        // 3. Eagle Eye Trigger via Double-Click
        function triggerEagleEye() {
            const password = prompt("Eagle Eye Verification Key enters karein, sweetie:");
            if (password === "eagleeye51") {
                toggleView('admin');
            } else if (password !== null) {
                alert("Wrong Key! Access Denied.");
            }
        }

        // 4. Toggle Views
        function toggleView(view) {
            if (view === 'admin') {
                document.getElementById('formSection').classList.add('hidden');
                document.getElementById('adminSection').classList.remove('hidden');
                listenToSubmissions();
            } else {
                document.getElementById('adminSection').classList.add('hidden');
                document.getElementById('formSection').classList.remove('hidden');
            }
        }

        // 5. Read Firebase Data
        function listenToSubmissions() {
            database.ref('auditions').on('value', (snapshot) => {
                const data = snapshot.val();
                allSubmissions = []; // Reset local array

                if (data) {
                    Object.keys(data).forEach(key => {
                        allSubmissions.push(data[key]);
                    });
                }
                renderTable(allSubmissions);
            }, (error) => {
                document.getElementById('adminTableBody').innerHTML = `<tr><td colspan="5" style="text-align: center; color: red;">Permission Denied. Set rules to public!</td></tr>`;
            });
        }

        // 6. Render Table data with Dynamic Whatsapp shortlisting text
        function renderTable(dataArray) {
            const tableBody = document.getElementById('adminTableBody');
            tableBody.innerHTML = '';

            if (dataArray.length === 0) {
                tableBody.innerHTML = `<tr><td colspan="5" style="text-align: center; color: #888;">No submissions match the filters.</td></tr>`;
                return;
            }

            dataArray.forEach(submission => {
                const row = document.createElement('tr');
                
                // Formatting custom Whatsapp shortlisting message
                const msg = encodeURIComponent(`Hi ${submission.name}! Hope you are doing well. This is SAM Events & Production. We checked your casting profile and would love to invite you for auditions!`);
                const waLink = `https://wa.me/${submission.phone}?text=${msg}`;

                row.innerHTML = `
                    <td><img src="${submission.photo}" class="preview-img" alt="Photo"></td>
                    <td>${submission.name}</td>
                    <td>${submission.age}</td>
                    <td><span class="badge">${submission.category}</span></td>
                    <td><a href="${waLink}" target="_blank" class="whatsapp-link">WhatsApp</a></td>
                `;
                tableBody.appendChild(row);
            });
        }

        // 7. Filtering and Searching logic
        function filterData() {
            const searchValue = document.getElementById('searchName').value.toLowerCase();
            const categoryValue = document.getElementById('filterCategory').value;

            const filtered = allSubmissions.filter(item => {
                const matchesName = item.name.toLowerCase().includes(searchValue);
                const matchesCategory = (categoryValue === 'all') || (item.category === categoryValue);
                return matchesName && matchesCategory;
            });

            renderTable(filtered);
        }
    </script>
</body>
</html>
