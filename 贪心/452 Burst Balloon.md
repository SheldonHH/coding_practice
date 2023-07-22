---
created: 2023-07-22 03:11:20
---
```cpp
#include <vector>
#include <algorithm>

using namespace std;

class Solution {
public:
    int findMinArrowShots(vector<vector<int>>& points) {
        if (points.empty()) {
            return 0;
        }

        // Sort the points by the end coordinate
        sort(points.begin(), points.end(), [](const vector<int>& a, const vector<int>& b) {
            return a[1] < b[1];
        });

        int arrow_count = 1;
        int current_arrow_end = points[0][1];

        for (int i = 1; i < points.size(); i++) {
            // If the start of the current point is greater than the end of the last shot arrow, we need another arrow
            if (points[i][0] > current_arrow_end) {
                arrow_count++;
                current_arrow_end = points[i][1];
            }
        }

        return arrow_count;
    }
};

```