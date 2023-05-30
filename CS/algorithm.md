- [이진탐색]
- [퀵정렬]
- [DFS]
- [BFS]
- [DP]
- [두_포인터]
- [슬라이딩_윈도우]
- [그리디_알고리즘]
- [리커시브]
- [백트래킹]
- [비트마스크]

<br>
<hr>
<br>

## @ 이진탐색 (Binary Search)

### `정렬된 상태에서 중간값과 목표값을 비교, 목표값의`
### `존재 유무를 탐색 범위를 절반씩 줄여나가 찾는 방법`

```javascript
function binarySearch(arr, x) {
    let start = 0, end = arr.length - 1;

    while (start <= end) {
        let mid = Math.floor((start + end) / 2);

        if (arr[mid] === x) return true;
        else if (arr[mid] < x) start = mid + 1;
        else end = mid - 1;
    }

    return false;
}
```

<br>

## @ 퀵 정렬 (Quick Sort)

### `pivot 을 정하여 해당 기준으로 작은 값은`
### `왼쪽, 큰 값은 오른쪽으로 이동시키는 방법`

```javascript
function quickSort(arr) {
    if (arr.length < 2) return arr;

    let pivot = arr[0];
    let lesser = arr.slice(1).filter(x => x < pivot);
    let greater = arr.slice(1).filter(x => x > pivot);

    return quickSort(lesser).concat(pivot, quickSort(greater));
}
```

<br>

## @ 깊이 우선 탐색 (DFS)

### `트리나 그래프에서`
### `깊이를 우선하여 탐색하는 방법(스택 or 재귀)`

```javascript
function dfs(graph, start) {
    let visited = [];
    let stack = [start];

    while (stack.length) {
        let node = stack.pop();
        if (visited.includes(node)) continue;
        visited.push(node);
        stack.push(...graph[node]);
    }

    return visited;
}
```

<br>

## @ 너비 우선 탐색 (BFS)

### `트리나 그래프에서`
### `너비를 우선하여 탐색하는 방법(큐)`

```javascript
function bfs(graph, start) {
    let visited = [];
    let queue = [start];

    while (queue.length) {
        let node = queue.shift();
        if (visited.includes(node)) continue;
        visited.push(node);
        queue.push(...graph[node]);
    }

    return visited;
}
```

<br>

## @ DP (Dynamic Programming)

### `복잡한 문제를 간단한 여러 개의`
### `문제로 나누어 푸는 방법(점화식)`

```javascript
function fibonacci(n, memo = {}) {
    if (n in memo) return memo[n];
    if (n <= 2) return 1;
    memo[n] = fibonacci(n - 1, memo) + fibonacci(n - 2, memo);
    return memo[n];
}
```

<br>

## @ 두 포인터 (Two Pointers)

### `배열을 동시에 두 포인터로 탐색하는 방법`

```javascript
function twoSum(arr, target) {
    let left = 0, right = arr.length - 1;

    while (left < right) {
        let sum = arr[left] + arr[right];
        if (sum === target) return [left, right];
        else if (sum < target) left++;
        else right--;
    }

    return [-1, -1];  // target을 만드는 두 수가 없는 경우
}
```

<br>

## @ 슬라이딩 윈도우 (Sliding Window)

### `배열에서 일정한 크기의 부분 배열(window)를`
### `이동시키면서 문제를 해결하는 방법`

```javascript
function maxSum(arr, k) {
    let maxSum = 0;
    let windowSum = 0;

    for(let i = 0; i < k; i++) {
        windowSum += arr[i];
    }

    for(let i = k; i < arr.length; i++) {
        windowSum += arr[i] - arr[i - k];
        maxSum = Math.max(maxSum, windowSum);
    }

    return maxSum;
}
```

<br>

## @ 그리디 알고리즘 (Greedy Algorithm)

### `문제를 해결하는 과정에서 그 순간순간마다`
### `최적이라고 생각되는 결정을 하는 방법`

```javascript
function minimumCoins(coins, target) {
    coins.sort((a, b) => b - a);

    let count = 0;
    for(let coin of coins) {
        if (target === 0) return count;
        count += Math.floor(target / coin);
        target %= coin;
    }

    return -1;  // target을 만드는 동전의 조합이 없는 경우
}
```

<br>

## @ 리커시브 (Recursive)

### `함수가 자기 자신을 호출하는 방식으로`
### `반복문의 역할을 수행하면서 더 복잡한 문제를 해결`

```javascript
function factorial(n) {
    if (n === 0) return 1;
    return n * factorial(n - 1);
}
```

<br>

## @ 백트래킹 (Backtracking)

### `여러 경로를 탐색하다가, 현재의 경로가 해결이 불가능하면`
### `이전 단계로 돌아가 다른 경로를 탐색하는 알고리즘`

```javascript
function permute(nums) {
    let result = [];
    backtrack([], nums, result);
    return result;
}

function backtrack(temp, nums, result) {
    if (temp.length === nums.length) {
        result.push([...temp]);
        return;
    }

    for(let num of nums) {
        if (temp.includes(num)) continue;
        temp.push(num);
        backtrack(temp, nums, result);
        temp.pop();
    }
}
```

## @ 비트마스크 (Bit Mask)

### `이진수를 사용하는 컴퓨터의 연산을 이용하여`
### `비트(bit)를 직접 조작하는 알고리즘 기법`

```javascript
//  AND(&), OR(|), XOR(^), NOT(~), 
// Left Shift(<<), Right Shift(>>)

//  주어진 숫자 배열(nums)의 모든 부분 집합(subsets)을 생성하는 예제입니다. 부분 집합은 비트마스크를 사용하여 나타내는 문제
function subsets(nums) {
    let result = [];
    let n = nums.length;
    let total = 1 << n;  // 2^n

    for(let i = 0; i < total; i++) {
        let subset = [];
        for(let j = 0; j < n; j++) {
            if(i & (1 << j)) subset.push(nums[j]);  // check if jth bit is set in i
        }
        result.push(subset);
    }

    return result;
}
```
