<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Algorithms</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/prism/1.24.1/themes/prism-okaidia.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/prism/1.24.1/plugins/line-numbers/prism-line-numbers.min.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.24.1/prism.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.24.1/plugins/line-numbers/prism-line-numbers.min.js"></script>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 20px;
            background-color: #f4f4f4;
        }

        h2 {
            color: #333;
        }

        .code-container {
            margin-bottom: 20px;
            background-color: #222;
            border-radius: 8px;
            overflow: hidden;
        }

        .code-editor {
            height: 200px;
            font-size: 14px;
            line-height: 1.5;
            color: #fff;
            padding: 15px;
            box-sizing: border-box;
            overflow: auto;
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
        <textarea id="fibonacciRecursiveCode" class="code-editor language-javascript line-numbers">function fibonacciRecursive(n) {
    if (n <= 1) return n;
    return fibonacciRecursive(n - 1) + fibonacciRecursive(n - 2);
}</textarea>
        <button onclick="runFibonacciRecursive()">Run</button>
    </div>

    <h2>Fibonacci Iterative Algorithm</h2>
    <div class="code-container">
        <textarea id="fibonacciIterativeCode" class="code-editor language-javascript line-numbers">function fibonacciIterative(n) {
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
        <textarea id="fibonacciMemoizationCode" class="code-editor language-javascript line-numbers">function fibonacciMemoization(n, memo = {}) {
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
        <textarea id="mergeSortCode" class="code-editor language-javascript line-numbers">function mergeSort(arr) {
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
        <textarea id="bubbleSortCode" class="code-editor language-javascript line-numbers">function bubbleSort(arr) {
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

    <h2>Binary Search</h2>
    <div class="code-container">
        <textarea id="binarySearchCode" class="code-editor language-javascript line-numbers">function binarySearch(arr, target) {
    let low = 0;
    let high = arr.length - 1;

    while (low <= high) {
        const mid = Math.floor((low + high) / 2);

        if (arr[mid] === target) {
            return mid; // Target found
        } else if (arr[mid] < target) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }

    return -1; // Target not found
}</textarea>
        <button onclick="runBinarySearch()">Run</button>
    </div>

    <script>
        // (Previous code remains unchanged)

        Prism.highlightAll();

        // Additional function to refresh Prism after updating code
        function refreshPrism() {
            Prism.highlightAll();
        }
    </script>
</body>
</html>
