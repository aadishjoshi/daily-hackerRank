# Insertion sort 2

https://www.hackerrank.com/challenges/insertionsort2/submissions/code/94858608


```

'use strict';

process.stdin.resume();
process.stdin.setEncoding('utf-8');

let inputString = '';
let currentLine = 0;

process.stdin.on('data', inputStdin => {
    inputString += inputStdin;
});

process.stdin.on('end', _ => {
    inputString = inputString.replace(/\s*$/, '')
        .split('\n')
        .map(str => str.replace(/\s*$/, ''));

    main();
});

function readLine() {
    return inputString[currentLine++];
}

// Complete the insertionSort2 function below.
function insertionSort2(n, arr) {
    for (let i = 1; i < n; i++) {
        for (let j = 0; j < i; j++) {
            if (arr[j] > arr[i]) {
                const temp = arr[j];
                arr[j] = arr[i];
                arr[i] = temp;
            }
        }
        process.stdout.write(arr.join(' ') + '\n');
    }

}

function main() {
    const n = parseInt(readLine(), 10);

    const arr = readLine().split(' ').map(arrTemp => parseInt(arrTemp, 10));

    insertionSort2(n, arr);
}



```