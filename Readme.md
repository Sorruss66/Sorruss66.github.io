Try2
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Data Formatter</title>
    <style>
        /* Your styles here */
    </style>
</head>
<body>
    <header>
        <h1>Data Formatter</h1>
    </header>
    <div class="container">
        <label for="dataInput">Enter Data:</label>
        <textarea id="dataInput" rows="10" placeholder="Enter data here..."></textarea>
        <button id="formatButton">Format Data</button>
        <h2>Formatted Data:</h2>
        <textarea id="formattedData" rows="10" readonly></textarea>
        <button id="copyButton">Copy to Clipboard</button>
    </div>

    <script>
        document.getElementById('formatButton').addEventListener('click', function () {
            const inputData = document.getElementById('dataInput').value;
            const formattedData = formatData(inputData);
            displayFormattedData(formattedData);
        });

        document.getElementById('copyButton').addEventListener('click', function () {
            const formattedData = document.getElementById('formattedData').value;
            copyToClipboard(formattedData);
        });

        function formatData(inputData) {
            // Split the input into lines
            const lines = inputData.split('\n');
            // Process each line
            const formattedLines = lines.map(line => {
                // Split the line by tabs
                const cells = line.split('\t');
                // Perform transformations on cells as needed
                const transformedCells = [
                    cells[0], // WIP
                    cells[1], // WL Date in
                    cells[2].trim(), // Registn
                    // Add other transformations for each cell here
                ];
                // Join the transformed cells with tabs
                return transformedCells.join('\t');
            });
            // Join the formatted lines with line breaks
            return formattedLines.join('\n');
        }

        function displayFormattedData(formattedData) {
            const formattedDataTextarea = document.getElementById('formattedData');
            formattedDataTextarea.value = formattedData;
        }

        function copyToClipboard(text) {
            const textarea = document.createElement('textarea');
            textarea.textContent = text;
            document.body.appendChild(textarea);
            textarea.select();
            document.execCommand('copy');
            document.body.removeChild(textarea);
            alert('Formatted data copied to clipboard');
        }
    </script>
</body>
</html>
