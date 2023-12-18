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
    if (n <= 1) return n;
    return fibonacciRecursive(n - 1) + fibonacciRecursive(n - 2);
}</textarea>
        <button onclick="runFibonacciRecursive()">Run</button>
    </div>

    <h2>Fibonacci Iterative Algorithm</h2>
    <div class="code-container">
        <textarea id="fibonacciIterativeCode" class="code-editor">function fibonacciIterative(n) {
    if (n <= 1) return n;

    let fib = [0, 1];
    for (let i = 2; i <= n; i++) {
        fib[i] = fib[i - 1] + fib[i - 2];
    }

    return fib[n];
}</textarea>
        <button onclick="runFibonacciIterative()">Run</button>
    </div>

    <h2>Fibonacci Memoization Algorithm</h2>
    <div class="code-container">
        <textarea id="fibonacciMemoizationCode" class="code-editor">function fibonacciMemoization(n, memo = {}) {
    if (n <= 1) return n;

    if (!memo.hasOwnProperty(n)) {
        memo[n] = fibonacciMemoization(n - 1, memo) + fibonacciMemoization(n - 2, memo);
    }

    return memo[n];
}</textarea>
        <button onclick="runFibonacciMemoization()">Run</button>
    </div>

    <h2>Merge Sorting</h2>
    <div class="code-container">
        <textarea id="mergeSortCode" class="code-editor">function mergeSort(arr) {
    if (arr.length <= 1) return arr;

    const middle = Math.floor(arr.length / 2);
    const left = arr.slice(0, middle);
    const right = arr.slice(middle);

    return merge(mergeSort(left), mergeSort(right));
}

function merge(left, right) {
    let result = [];
    let i = 0;
    let j = 0;

    while (i < left.length && j < right.length) {
        if (left[i] < right[j]) {
            result.push(left[i]);
            i++;
        } else {
            result.push(right[j]);
            j++;
        }
    }

    return result.concat(left.slice(i)).concat(right.slice(j));
}</textarea>
        <button onclick="runMergeSort()">Run</button>
    </div>

    <h2>Bubble Sorting</h2>
    <div class="code-container">
        <textarea id="bubbleSortCode" class="code-editor">function bubbleSort(arr) {
    const n = arr.length;

    for (let i = 0; i < n - 1; i++) {
        for (let j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap arr[j] and arr[j + 1]
                const temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }

    return arr;
}</textarea>
        <button onclick="runBubbleSort()">Run</button>
    </div>
        <button onclick="runBinarySort()">Run</button>
    </div>

    <script>
        function runFibonacciRecursive() {
            const code = document.getElementById('fibonacciRecursiveCode').value;
            const n = 5; // Example input
            const result = eval(`${code} fibonacciRecursive(${n})`);
            alert(`Result: ${result}`);
        }

        function runFibonacciIterative() {
            const code = document.getElementById('fibonacciIterativeCode').value;
            const n = 5; // Example input
            const result = eval(`${code} fibonacciIterative(${n})`);
            alert(`Result: ${result}`);
        }

        function runFibonacciMemoization() {
            const code = document.getElementById('fibonacciMemoizationCode').value;
            const n = 5; // Example input
            const result = eval(`${code} fibonacciMemoization(${n})`);
            alert(`Result: ${result}`);
        }
    </script>
</body>
</html>
