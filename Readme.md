<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Service Data Formatter</title>
    <style>
        table {
            border-collapse: collapse;
            width: 100%;
        }

        th, td {
            border: 1px solid #ddd;
            padding: 8px;
            text-align: left;
        }

        th {
            background-color: #f2f2f2;
        }
    </style>
</head>
<body>
    <header>
        <h1>Service Data Formatter</h1>
    </header>
    <div class="container">
        <label for="serviceData">Enter Service Data:</label>
        <textarea id="serviceData" rows="10" placeholder="Enter Service Data here..."></textarea>
        <button id="formatButton">Format Data</button>
        <h2>Formatted Data:</h2>
        <div id="formattedData"></div>
        <button id="copyButton">Copy to Clipboard</button>
    </div>

    <script>
        document.getElementById('formatButton').addEventListener('click', function () {
            const input = document.getElementById('serviceData').value;
            const formattedData = formatData(input);
            displayFormattedData(formattedData);
        });

        document.getElementById('copyButton').addEventListener('click', function () {
            const formattedData = document.getElementById('formattedData').innerHTML;
            copyToClipboard(formattedData);
        });

        function formatData(input) {
            const lines = input.split('\n').map(line => line.trim());
            const headers = ["WIP", "WL Date in", "Registn", "CSC", "Customer name", "Model code", "S", "RTS", "TYP", "WL Str Dte", "Time", "Count", "Date due in", "Free text"];
            const formattedLines = lines.map(line => line.split(/\s{2,}/));
            return { headers, rows: formattedLines };
        }

        function displayFormattedData(formattedData) {
            const table = document.createElement('table');

            // Add headers
            const headerRow = table.insertRow();
            formattedData.headers.forEach(header => {
                const th = document.createElement('th');
                th.textContent = header;
                headerRow.appendChild(th);
            });

            // Add rows
            formattedData.rows.forEach(rowData => {
                const row = table.insertRow();
                rowData.forEach(cellData => {
                    const cell = row.insertCell();
                    cell.textContent = cellData;
                });
            });

            const formattedDataDiv = document.getElementById('formattedData');
            formattedDataDiv.innerHTML = '';
            formattedDataDiv.appendChild(table);
        }

        function copyToClipboard(text) {
            const textarea = document.createElement('textarea');
            textarea.textContent = text;
            document.body.append(textarea);
            textarea.select();
            document.execCommand('copy');
            document.body.removeChild(textarea);
            alert('Formatted data copied to clipboard');
        }
    </script>
</body>
</html>
