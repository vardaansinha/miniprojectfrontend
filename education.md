<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Algorithms</title>
    <link rel="stylesheet" href="https://codemirror.net/lib/codemirror.css">
    <script src="https://codemirror.net/lib/codemirror.js"></script>
    <script src="https://codemirror.net/mode/clike/clike.js"></script>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 20px;
        }

        h2 {
            color: #333;
        }

        .code-container {
            margin-bottom: 20px;
        }

        .code-editor {
            height: 200px;
        }

        button {
            padding: 8px 16px;
            font-size: 14px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <h2>Fibonacci Recursive Algorithm</h2>
    <div class="code-container">
        <textarea id="fibonacciRecursiveCode" class="code-editor">function fibonacciRecursive(n) {
    // Your code here
}</textarea>
        <button onclick="runFibonacciRecursive()">Run</button>
    </div>

    <h2>Fibonacci Iterative Algorithm</h2>
    <div class="code-container">
        <textarea id="fibonacciIterativeCode" class="code-editor">function fibonacciIterative(n) {
    // Your code here
}</textarea>
        <button onclick="runFibonacciIterative()">Run</button>
    </div>

    <h2>Fibonacci Memoization Algorithm</h2>
    <div class="code-container">
        <textarea id="fibonacciMemoizationCode" class="code-editor">function fibonacciMemoization(n, memo = {}) {
    // Your code here
}</textarea>
        <button onclick="runFibonacciMemoization()">Run</button>
    </div>

    <h2>Merge Sorting</h2>
    <div class="code-container">
        <textarea id="mergeSortCode" class="code-editor">function mergeSort(arr) {
    // Your code here
}</textarea>
        <button onclick="runMergeSort()">Run</button>
    </div>

    <h2>Bubble Sorting</h2>
    <div class="code-container">
        <textarea id="bubbleSortCode" class="code-editor">function bubbleSort(arr) {
    // Your code here
}</textarea>
        <button onclick="runBubbleSort()">Run</button>
    </div>

    <h2>Binary Sorting</h2>
    <div class="code-container">
        <textarea id="binarySortCode" class="code-editor">function binarySort(arr) {
    // Your code here
}</textarea>
        <button onclick="runBinarySort()">Run</button>
    </div>

    <script>
        function runFibonacciRecursive() {
            const code = document.getElementById('fibonacciRecursiveCode').value;
            eval(code);
            // Call the function with an example input if needed
            // fibonacciRecursive(5);
        }

        function runFibonacciIterative() {
            const code = document.getElementById('fibonacciIterativeCode').value;
            eval(code);
            // Call the function with an example input if needed
            // fibonacciIterative(5);
        }

        function runFibonacciMemoization() {
            const code = document.getElementById('fibonacciMemoizationCode').value;
            eval(code);
            // Call the function with an example input if needed
            // fibonacciMemoization(5);
        }

        function runMergeSort() {
            const code = document.getElementById('mergeSortCode').value;
            eval(code);
            // Call the function with an example input if needed
            // mergeSort([3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]);
        }

        function runBubbleSort() {
            const code = document.getElementById('bubbleSortCode').value;
            eval(code);
            // Call the function with an example input if needed
            // bubbleSort([3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]);
        }

        function runBinarySort() {
            const code = document.getElementById('binarySortCode').value;
            eval(code);
            // Call the function with an example input if needed
            // binarySort([3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]);
        }
    </script>
</body>
</html>
