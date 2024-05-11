<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CB5 Formatter</title>
    <style>
        /* Your existing styles */
    </style>
</head>
<body>
    <header>
        <h1>CB5 Formatter</h1>
    </header>
    <div class="container">
        <label for="jsonInput">Enter Data:</label>
        <textarea id="jsonInput" rows="10" placeholder="Enter Data here..."></textarea>
        <button id="formatButton">Click Here to Continue</button>
        <h2>Formatted Data:</h2>
        <textarea id="formattedJSON" rows="10" readonly></textarea>
        <button id="copyButton">Copy to Clipboard</button>
    </div>

    <script>
        document.getElementById('formatButton').addEventListener('click', function () {
            const inputJSON = document.getElementById('jsonInput').value;
            const formattedJSON = formatJSON(inputJSON);
            displayFormattedJSON(formattedJSON);
        });

        document.getElementById('copyButton').addEventListener('click', function () {
            const formattedJSON = document.getElementById('formattedJSON').value;
            copyToClipboard(formattedJSON);
        });

        function formatJSON(inputJSON) {
            try {
                const parsedJSON = JSON.parse(inputJSON);
                return JSON.stringify(parsedJSON, null, 2);
            } catch (error) {
                return "Invalid JSON!";
            }
        }

        function displayFormattedJSON(formattedJSON) {
            const formattedJSONTextarea = document.getElementById('formattedJSON');
            formattedJSONTextarea.value = formattedJSON;
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
