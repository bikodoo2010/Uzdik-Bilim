# 1. Екілік іздеу
```
def binary_search_first_ge(arr, x):
    left, right = 0, len(arr) - 1
    answer = -1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] >= x:
            answer = mid
            right = mid - 1
        else:
            left = mid + 1
    return answer

a = [1, 3, 3, 5, 7]
print(binary_search_first_ge(a, 4))  # Вывод: 3 (элемент 5)
```
# 2. Префикс - Суффикс
```
a = [1, 2, 3, 4, 5]
n = len(a)
pref = [0] * (n+1)
for i in range(n):
    pref[i+1] = pref[i] + a[i]

# сумма от 1 до 3 (индексы 1..3)
l, r = 1, 3
sum_lr = pref[r+1] - pref[l]  # 2+3+4=9
print(sum_lr)
```
# 3. Екі көрсеткіш
```
a = [1, 2, 3, 4, 5]
a.sort()
x = 5
l, r = 0, len(a)-1
count = 0

while l < r:
    if a[l] + a[r] <= x:
        count += r - l
        l += 1
    else:
        r -= 1
print(count)  # Вывод: 6
```
# 4. Үйме - Heapq
```
import heapq

a = [5, 1, 3, 2]
heapq.heapify(a)  # превращаем в min-heap

heapq.heappush(a, 0)  # добавляем элемент
print(heapq.heappop(a))  # извлекаем минимум (0)
```
# 5. ДП - Рекурсия
```
memo = {}
def fib(n):
    if n <= 1:
        return n
    if n in memo:
        return memo[n]
    memo[n] = fib(n-1) + fib(n-2)
    return memo[n]

print(fib(10))  # 55
```


# 6. ДП - Табуляция-Кестелік
```
n = 10
dp = [0] * (n+1)
dp[1] = 1
for i in range(2, n+1):
    dp[i] = dp[i-1] + dp[i-2]
print(dp[n])  # 55
```
# 7. Бит-маска
```
arr = [1, 2, 3]
n = len(arr)
for mask in range(1<<n):
    subset = [arr[i] for i in range(n) if mask & (1<<i)]
    print(subset)
```
# 8. Графтар теориясы
```
from collections import deque

graph = {0: [1,2], 1: [0,2], 2: [0,1,3], 3:[2]}
visited = set()
queue = deque([0])

while queue:
    node = queue.popleft()
    if node in visited:
        continue
    visited.add(node)
    print(node)
    for neighbor in graph[node]:
        if neighbor not in visited:
            queue.append(neighbor)
```
# 9. 2D массив - BFS-DFS
```
grid = [
    [1,1,0],
    [0,1,0],
    [1,0,1]
]

def dfs(i,j):
    if i<0 or j<0 or i>=len(grid) or j>=len(grid[0]) or grid[i][j]==0:
        return
    grid[i][j] = 0
    dfs(i+1,j); dfs(i-1,j); dfs(i,j+1); dfs(i,j-1)

count = 0
for i in range(len(grid)):
    for j in range(len(grid[0])):
        if grid[i][j] == 1:
            dfs(i,j)
            count += 1
print(count)  # 3 острова
```
