

# Intuition

A clock is a circle of **360°**, and both hands move continuously.

The key detail is that the **hour hand never stays fixed**.

At **3:30**, many people think the hour hand is still exactly on **3** (which corresponds to **90°** from 12).

However, after 30 minutes, the hour hand has already moved halfway toward **4**, placing it at **105°**.

That small movement is what makes the difference.

---


### 🎯 Key Observation

Imagine freezing the clock every minute:

* Minute hand moves **6° per minute**
* Hour hand moves **0.5° per minute**

Even though it's harder to notice, the hour hand is always moving.

That's the entire trick behind this problem.

---

# Approach

### Step 1: Find the Position of the Hour Hand

The hour hand completes:

* **360° in 12 hours**
* Therefore **30° per hour**

Since it moves continuously:

* **30° in 60 minutes**
* Therefore **0.5° per minute**

Formula:

```text
hourAngle = 30 × hour + 0.5 × minutes
```

---

### Step 2: Find the Position of the Minute Hand

The minute hand completes:

* **360° in 60 minutes**
* Therefore **6° per minute**

Formula:

```text
minuteAngle = 6 × minutes
```

---

### Step 3: Compute the Difference

The angle between the hands is:

```text
diff = |hourAngle - minuteAngle|
```

Substituting the formulas:

```text
diff = |(30 × hour + 0.5 × minutes) - (6 × minutes)|
```

Simplifying:

```text
diff = |30 × hour - 5.5 × minutes|
```

The famous **5.5** comes from:

```text
6 - 0.5 = 5.5
```

---

### Step 4: Return the Smaller Angle

The hands divide the clock into two angles:

* `diff`
* `360 - diff`

We return the smaller one:

```text
answer = min(diff, 360 - diff)
```

---

# Dry Run

### Example

```text
hour = 3
minutes = 30
```

Hour hand:

```text
30 × 3 + 0.5 × 30
= 90 + 15
= 105°
```

Minute hand:

```text
6 × 30
= 180°
```

Difference:

```text
|105 - 180|
= 75°
```

Other angle:

```text
360 - 75
= 285°
```

Final Answer:

```text
75°
```

✅ Correct Answer

---

# Complexity Analysis

### Time Complexity

```text
O(1)
```

Only a few arithmetic operations are performed.

### Space Complexity

```text
O(1)
```

No extra memory is used.

---

# Code

## 🐍 Python

```python
class Solution:
    def angleClock(self, hour: int, minutes: int) -> float:

        hour_angle = 30 * hour + 0.5 * minutes
        minute_angle = 6 * minutes

        diff = abs(hour_angle - minute_angle)

        return min(diff, 360 - diff)
```

## ⚡ C++

```cpp
class Solution {
public:
    double angleClock(int hour, int minutes) {

        double hourAngle = 30.0 * hour + 0.5 * minutes;
        double minuteAngle = 6.0 * minutes;

        double diff = abs(hourAngle - minuteAngle);

        return min(diff, 360.0 - diff);
    }
};
```

## ☕ Java

```java
class Solution {
    public double angleClock(int hour, int minutes) {

        double hourAngle = 30.0 * hour + 0.5 * minutes;
        double minuteAngle = 6.0 * minutes;

        double diff = Math.abs(hourAngle - minuteAngle);

        return Math.min(diff, 360.0 - diff);
    }
}
```

## 🟨 JavaScript

```javascript
/**
 * @param {number} hour
 * @param {number} minutes
 * @return {number}
 */
var angleClock = function(hour, minutes) {

    const hourAngle = 30 * hour + 0.5 * minutes;
    const minuteAngle = 6 * minutes;

    const diff = Math.abs(hourAngle - minuteAngle);

    return Math.min(diff, 360 - diff);
};
```

## 🐹 Go

```go
import "math"

func angleClock(hour int, minutes int) float64 {

    hourAngle := 30.0*float64(hour) + 0.5*float64(minutes)
    minuteAngle := 6.0 * float64(minutes)

    diff := math.Abs(hourAngle - minuteAngle)

    return math.Min(diff, 360.0-diff)
}
```


