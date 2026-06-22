# 🚀 Maximum Number of "Balloon" Instances from a String

📌 Topics: Hash Table, String  
💡 Languages: Python, C++, Java, JavaScript, Go  

---

## 🧠 Intuition

We are given a string and need to find how many times we can form the word **"balloon"**.

Each character has a required frequency:

- `b → 1`
- `a → 1`
- `l → 2`
- `o → 2`
- `n → 1`

👉 The answer is limited by the **minimum available characters** after accounting for frequency requirements.

---

## 🧩 Approach

- Count frequency of each character in the string
- Compute how many times "balloon" can be formed
- Take minimum among required characters
- Special case: `l` and `o` are divided by 2

---

## 📌 Key Insight

The **bottleneck character** determines the final answer.

---

## ⏱ Complexity Analysis

- **Time Complexity:** `O(n)`
- **Space Complexity:** `O(1)` (fixed 26-letter array / small map)

---

## 💻 Code (All Languages in One Place)

```python []
from collections import Counter

class Solution:
    def maxNumberOfBalloons(self, text: str) -> int:
        freq = Counter(text)

        return min(
            freq['b'],
            freq['a'],
            freq['l'] // 2,
            freq['o'] // 2,
            freq['n']
        )
```

```C++ []
// C++
#include <bits/stdc++.h>
using namespace std;

class Solution {
public:
    int maxNumberOfBalloons(string text) {
        vector<int> freq(26, 0);

        for (char c : text) freq[c - 'a']++;

        return min({
            freq['b' - 'a'],
            freq['a' - 'a'],
            freq['l' - 'a'] / 2,
            freq['o' - 'a'] / 2,
            freq['n' - 'a']
        });
    }
};
```

```Java []
// Java
class Solution {
    public int maxNumberOfBalloons(String text) {
        int[] freq = new int[26];

        for (char c : text.toCharArray()) {
            freq[c - 'a']++;
        }

        return Math.min(
            Math.min(freq['b' - 'a'], freq['a' - 'a']),
            Math.min(freq['l' - 'a'] / 2,
            Math.min(freq['o' - 'a'] / 2, freq['n' - 'a']))
        );
    }
}
```

```JS []
// JavaScript
var maxNumberOfBalloons = function(text) {
    let freq = new Array(26).fill(0);

    for (let c of text) {
        freq[c.charCodeAt(0) - 97]++;
    }

    return Math.min(
        freq['b'.charCodeAt(0) - 97],
        freq['a'.charCodeAt(0) - 97],
        Math.floor(freq['l'.charCodeAt(0) - 97] / 2),
        Math.floor(freq['o'.charCodeAt(0) - 97] / 2),
        freq['n'.charCodeAt(0) - 97]
    );
};
```

```Go []
// Go
package main

func maxNumberOfBalloons(text string) int {
    freq := make(map[rune]int)

    for _, c := range text {
        freq[c]++
    }

    return min(
        freq['b'],
        freq['a'],
        freq['l']/2,
        freq['o']/2,
        freq['n'],
    )
}

func min(vals ...int) int {
    m := vals[0]
    for _, v := range vals {
        if v < m {
            m = v
        }
    }
    return m
}
```