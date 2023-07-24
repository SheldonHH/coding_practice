# python
```python
from collections import deque

class Solution:
    def numIslands(self, grid):
        if not grid:
            return 0

        count = 0
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if grid[i][j] == '1':
                    self.bfs(grid, i, j)
                    count += 1
        return count

    def bfs(self, grid, i, j):
        queue = deque([(i, j)])
        while queue:
            i, j = queue.popleft()
            if 0 <= i < len(grid) and 0 <= j < len(grid[0]) and grid[i][j] == '1':
                grid[i][j] = '0'
                queue.extend([(i-1, j), (i+1, j), (i, j-1), (i, j+1)])

```


# BFS cpp
```cpp
#include <queue>

class Solution {
public:
    int numIslands(vector<vector<char>>& grid) {
        if (grid.empty() || grid[0].empty()) {
            return 0;
        }
        int islands = 0;
        for (int i = 0; i < grid.size(); i++) {
            for (int j = 0; j < grid[0].size(); j++) {
                if (grid[i][j] == '1') {
                    bfs(grid, i, j);
                    islands++;
                }
            }
        }
        return islands;
    }

private:
    void bfs(vector<vector<char>>& grid, int i, int j) {
        queue<pair<int, int>> q;
        q.push({i, j});
        while (!q.empty()) {
            tie(i, j) = q.front(); q.pop();
            if (i < 0 || j < 0 || i >= grid.size() || j >= grid[0].size() || grid[i][j] != '1') {
                continue;
            }
            grid[i][j] = '0';
            q.push({i - 1, j});
            q.push({i + 1, j});
            q.push({i, j - 1});
            q.push({i, j + 1});
        }
    }
};

```


## BFS Rust
```rust
use std::collections::VecDeque;

pub struct Solution;

impl Solution {
    pub fn num_islands(mut grid: Vec<Vec<char>>) -> i32 {
        let mut count = 0;
        let directions = [(0, 1), (0, -1), (1, 0), (-1, 0)];
        for i in 0..grid.len() {
            for j in 0..grid[0].len() {
                if grid[i][j] == '1' {
                    let mut queue: VecDeque<(usize, usize)> = VecDeque::new();
                    count += 1;
                    grid[i][j] = '0';
                    queue.push_back((i, j));

                    while let Some((row, col)) = queue.pop_front() {
                        for dir in &directions {
                            let new_row = row as i32 + dir.0;
                            let new_col = col as i32 + dir.1;

                            if new_row >= 0
                                && new_col >= 0
                                && new_row < grid.len() as i32
                                && new_col < grid[0].len() as i32
                                && grid[new_row as usize][new_col as usize] == '1'
                            {
                                queue.push_back((new_row as usize, new_col as usize));
                                grid[new_row as usize][new_col as usize] = '0';
                            }
                        }
                    }
                }
            }
        }
        count
    }
}

```