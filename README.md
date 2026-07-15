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

        .logo-area {
            text-align: center;
            margin-bottom: 25px;
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

        /* Navigation Button */
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
    </style>

    <!-- Firebase v9 Web Compatibility Scripts (Required for Single-Page HTML Deployment) -->
    <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-database-compat.js"></script>
</head>
<body>

    <!-- Main Registration Container -->
    <div class="container" id="formSection">
        <div class="logo-area">
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

        <button class="toggle-btn" onclick="toggleView('admin')">View Admin Panel</button>
    </div>

    <!-- Admin Panel Container -->
    <div class="container hidden" id="adminSection">
        <div class="logo-area">
            <h2>SAM EVENTS - ADMIN PANEL</h2>
            <p>Review Registered Talent (Realtime)</p>
        </div>

        <h3>Received Applications</h3>
        
        <div class="table-wrapper">
            <table>
                <thead>
                    <tr>
                        <th>Photo</th>
                        <th>Name</th>
                        <th>Age</th>
                        <th>Category</th>
                        <th>WhatsApp</th>
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
        // 1. Initialize Firebase using the Compat Library
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

        // 2. Form Submission to Firebase Realtime Database
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
                // Generate a unique push key under 'auditions' node
                const newAuditionRef = database.ref('auditions').push();
                
                newAuditionRef.set({
                    name: fullName,
                    age: age,
                    category: category,
                    phone: phone,
                    photo: reader.result // Photo base64 data url
                }).then(() => {
                    alert('Application successfully sent to Realtime Database, sweetie!');
                    document.getElementById('castingForm').reset();
                    submitBtn.innerText = "Submit Application";
                    submitBtn.disabled = false;
                }).catch((error) => {
                    alert('Error writing to database: ' + error.message);
                    submitBtn.innerText = "Submit Application";
                    submitBtn.disabled = false;
                });
            }

            if (file) {
                reader.readAsDataURL(file);
            }
        });

        // 3. Toggle View Function
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

        // 4. Listen to Realtime Submissions from Firebase
        function listenToSubmissions() {
            const tableBody = document.getElementById('adminTableBody');
            
            // Listen for any database changes live!
            database.ref('auditions').on('value', (snapshot) => {
                tableBody.innerHTML = '';
                const data = snapshot.val();

                if (!data) {
                    tableBody.innerHTML = `<tr><td colspan="5" style="text-align: center; color: #888;">No applications found in Firebase.</td></tr>`;
                    return;
                }

                // Render each node dynamically
                Object.keys(data).forEach(key => {
                    const submission = data[key];
                    const row = document.createElement('tr');
                    row.innerHTML = `
                        <td><img src="${submission.photo}" class="preview-img" alt="User Photo"></td>
                        <td>${submission.name}</td>
                        <td>${submission.age}</td>
                        <td><span class="badge">${submission.category}</span></td>
                        <td><a href="https://wa.me/${submission.phone}" target="_blank" style="color: #d4af37; text-decoration: none;">${submission.phone}</a></td>
                    `;
                    tableBody.appendChild(row);
                });
            }, (error) => {
                tableBody.innerHTML = `<tr><td colspan="5" style="text-align: center; color: red;">Permission Denied. Set rules to public!</td></tr>`;
            });
        }
    </script>
</body>
</html>
