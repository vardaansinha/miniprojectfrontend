<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fibonacci Algorithms</title>
    <link rel="stylesheet" href="styles.css">
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Lato:wght@400;700&display=swap">
</head>

<body>
    <style>
        body {
            font-family: 'Lato', sans-serif;
            background-color: #f7f9fc;
            margin: 0;
            padding: 0;
            color: #333;
        }

        .container {
            max-width: 650px;
            margin: 60px auto;
            background-color: #ffffff;
            padding: 40px;
            border-radius: 10px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
        }

        h1 {
            text-align: center;
            margin-bottom: 40px;
            color: #2c3e50;
            font-weight: 700;
        }

        .input-group {
            margin-bottom: 30px;
        }

        label {
            display: block;
            margin-bottom: 10px;
            font-weight: 600;
            color: #34495e;
        }

        input {
            width: 100%;
            padding: 14px;
            border: 1px solid #e0e0e0;
            border-radius: 8px;
            transition: border-color 0.3s, box-shadow 0.3s;
        }

        input:focus {
            border-color: #007BFF;
            box-shadow: 0 0 0 3px rgba(0, 123, 255, 0.1);
            outline: none;
        }

        button {
            display: block;
            width: 100%;
            padding: 14px;
            background-color: #007BFF;
            color: #fff;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.3s;
        }

        button:hover {
            background-color: #0056b3;
            transform: translateY(-2px);
        }

        #computation {
            font-size: 26px;
            color: #007BFF;
            margin-top: 30px;
            text-align: center;
            font-weight: 700;
        }

        #formula {
            font-size: 18px;
            color: #2c3e50;
            background-color: #f7f9fc;
            padding: 15px;
            border-radius: 8px;
            text-align: center;
            margin-bottom: 30px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
        }

        /* algorithm button styling */
        .algorithm-info {
            display: none;
            margin-top: 20px;
        }
    </style>

    <div class="container">
        <h1>Fibonacci Algorithms</h1>

        <div class="input-group">
            <button onclick="showAlgorithm('recursive')">Fibonacci Recursive</button>
            <button onclick="showAlgorithm('iterative')">Fibonacci Iterative</button>
            <button onclick="showAlgorithm('memoization')">Fibonacci Memoization</button>
        </div>

        <div id="recursive-info" class="algorithm-info">
            <h2>Recursive Algorithm</h2>
            <p>Information about the Fibonacci Recursive Algorithm goes here.</p>
        </div>

        <div id="iterative-info" class="algorithm-info">
            <h2>Iterative Algorithm</h2>
            <p>Information about the Fibonacci Iterative Algorithm goes here.</p>
        </div>

        <div id="memoization-info" class="algorithm-info">
            <h2>Memoization Algorithm</h2>
            <p>Information about the Fibonacci Memoization Algorithm goes here.</p>
        </div>

    </div>

    <script>
        // showing algorithm information
        function showAlgorithm(algorithm) {
            // hiding all of the algorithm information
            document.querySelectorAll('.algorithm-info').forEach(function (element) {
                element.style.display = 'none';
            });

            // on click
            document.getElementById(algorithm + '-info').style.display = 'block';
        }
    </script>
</body>

</html>


