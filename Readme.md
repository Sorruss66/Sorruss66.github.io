<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Service Data Formatter</title>
    <style>
        /* Your styles here */
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
        <textarea id="formattedData" rows="10" readonly></textarea>
        <button id="copyButton">Copy to Clipboard</button>
    </div>

    <script>
        document.getElementById('formatButton').addEventListener('click', function () {
            const input = document.getElementById('serviceData').value;
            const formattedData = formatData(input);
            displayFormattedData(formattedData);
        });

        document.getElementById('copyButton').addEventListener('click', function () {
            const formattedData = document.getElementById('formattedData').value;
            copyToClipboard(formattedData);
        });

        function formatData(input) {
            const lines = input.split('\n').map(line => line.trim());
            const headers = "WIP\tWL Date in\tRegistn\tCSC\tCustomer name\tModel code\tS\tRTS\tTYP\tWL Str Dte\tTime\tCount\tDate due in\tFree text";
            const formattedLines = lines.map(line => line.replace(/\t/g, '').replace(/\s+/g, '\t'));
            return headers + '\n' + formattedLines.join('\n');
        }

        function displayFormattedData(formattedData) {
            const formattedDataTextarea = document.getElementById('formattedData');
            formattedDataTextarea.value = formattedData;
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
