<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GitHub Stats Input</title>
    <link rel="stylesheet" href="styles.css">
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Lato:wght@400;700&display=swap">
</head>

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
        margin-bottom: 10px;
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
        /* This will create space between the formula and the images */
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
    }

    .explanation {
        display: none;
        margin-top: 20px;
    }
</style>

<body>
    <div class="container">
        <h1>Enter Your GitHub Stats</h1>
        <form id="githubStatsForm">
            <div class="input-group">
                <label for="commits">Commits:</label>
                <input type="number" id="commits" required>
            </div>
            <div class="input-group">
                <label for="pulls">Pull Requests:</label>
                <input type="number" id="pulls" required>
            </div>
            <div class="input-group">
                <label for="issues">Issues:</label>
                <input type="number" id="issues" required>
            </div>
            <div class="input-group">
                <label for="repos">Repositories Contributed To:</label>
                <input type="number" id="repos" required>
            </div>
            <button type="submit">Submit</button>
        </form>
        <div id="computation"></div>
        <div id="formula"></div>
        <div id="imageContainer"></div>

        <!-- Buttons for explaining concepts -->
        <button onclick="toggleExplanation('mergeSort')">Explain Merge Sort</button>
        <button onclick="toggleExplanation('binarySearch')">Explain Binary Search</button>
        <button onclick="toggleExplanation('bubbleSort')">Explain Bubble Sort</button>

        <!-- Explanation sections -->
        <div id="mergeSortExplanation" class="explanation">
            <h2>Merge Sort</h2>
            <p>Merge Sort is a divide-and-conquer algorithm that recursively divides an array into halves, sorts each half, and then merges them back together. This process continues until the entire array is sorted. It has a time complexity of O(n log n) and is stable.</p>
        </div>
        <div id="binarySearchExplanation" class="explanation">
            <h2>Binary Search</h2>
            <p>Binary Search is a searching algorithm used to find the position of a target element in a sorted array. It works by repeatedly dividing the array in half and comparing the target element with the middle element. It has a time complexity of O(log n).</p>
        </div>
        <div id="bubbleSortExplanation" class="explanation">
            <h2>Bubble Sort</h2>
            <p>Bubble Sort is a simple sorting algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. The pass through the list is repeated until the list is sorted. It has a time complexity of O(n^2) and is not recommended for large datasets.</p>
        </div>
    </div>

    <script>
        // Define the API endpoint URL
        const apiUrl = 'http://localhost:8085/api/grade/predict';

        document.getElementById('githubStatsForm').addEventListener('submit', function (event) {
            event.preventDefault();

            // Get values from the form
            const commits = document.getElementById('commits').value;
            const pulls = document.getElementById('pulls').value;
            const issues = document.getElementById('issues').value;
            const repos = document.getElementById('repos').value;

            // Create an object to store your request data
            const requestData = {
                "numStudents": 1000
            }

            // Define the fetch options, including the HTTP method and headers
            const fetchOptions = {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify(requestData)
            };

            // Make the API request using the fetch function
            fetch(apiUrl, fetchOptions)
                .then(response => {
                    if (!response.ok) {
                        throw new Error('Network response was not ok');
                    }
                    return response.json();
                })
                .then(data => {
                    // Compute the prediction using the returned coefficients
                    const prediction = data.bias +
                        (data.commitCoefficient * commits) +
                        (data.pullCoefficient * pulls) +
                        (data.issueCoefficient * issues) +
                        (data.reposContributedToCoefficient * repos);

                    // Display the computed prediction
                    document.getElementById('computation').textContent = `Predicted Score: ${prediction.toFixed(2)}`;

                    document.getElementById('formula').textContent = `Score = ${data.bias.toFixed(2)} + ${data.commitCoefficient.toFixed(2)} * Commits + ${data.pullCoefficient.toFixed(2)} * Pulls + ${data.issueCoefficient.toFixed(2)} * Issues + ${data.reposContributedToCoefficient.toFixed(2)} * Repos`;


                    const imageContainer = document.getElementById('imageContainer');
                    imageContainer.innerHTML = '';

                    // Display the chart images
                    const imageUrls = data.imageUrls;
                    imageUrls.forEach(url => {
                        const img = document.createElement('img');
                        img.src = "http://localhost:8085" + url;
                        document.getElementById('imageContainer').appendChild(img);
                    });
                })
                .catch(error => {
                    console.error('Error:', error);
                });
        });

        // Function to toggle explanation sections
        function toggleExplanation(algorithm) {
            // Toggle the visibility of the explanation section
            const explanation = document.getElementById(algorithm + 'Explanation');
            explanation.style.display = explanation.style.display === 'none' ? 'block' : 'none';
        }
    </script>
</body>

</html>
