Prepared By 
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CB5 Formatter </title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            margin: 0;
            padding: 0;
        }

        header {
            background-color: #0078d4;
            color: #fff;
            text-align: center;
            padding: 20px 0;
        }

        h1 {
            font-size: 36px;
        }

        .container {
            max-width: 800px;
            margin: 20px auto;
            padding: 20px;
            background-color: #fff;
            box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
            border-radius: 5px;
        }

        textarea {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            resize: vertical;
        }

        button {
            background-color: #0078d4;
            color: #fff;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
        }

        button:hover {
            background-color: #005a9e;
        }

        h2 {
            font-size: 24px;
            margin-top: 20px;
        }

        #formattedJSON {
            min-height: 100px;
        }
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
    </div>

    <script>
        document.getElementById('formatButton').addEventListener('click', function () {
            const inputJSON = document.getElementById('jsonInput').value;
            const formattedJSON = formatJSON(inputJSON);
            displayFormattedJSON(formattedJSON);
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
    </script>
</body>
</html>
