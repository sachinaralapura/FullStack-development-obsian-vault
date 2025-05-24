

**Definition:** This measures the amount of time an algorithm takes to run as a function of the input size (n). It's not about the actual time in seconds (which varies based on hardware, programming language, etc.), but rather the _number of operations_ the algorithm performs.

**Purpose:** It helps predict how an algorithm's running time will grow with larger inputs. For example, an algorithm that performs n operations will be faster than one that performs n2 operations for large n.

When an interviewer asks for the time complexity of a particular program, they are referring to how the runtime of an algorithm grows as the input size increases. We analyze algorithms based on their best, average, and worst-case time complexities.

---
### **Worst-Case, Best-Case, and Average-Case:**

- **Worst-Case:** The maximum time an algorithm will take for any input of a given size. This is usually the most important for guarantees. Represents the **upper bound** of an algorithm's running time. It describes the worst-case scenario for the algorithm's growth rate as the input size increases.

- **Best-Case:** The minimum time an algorithm will take. This is often not very useful in practice as it might only occur for specific, ideal inputs.Represents the **lower bound** of an algorithm's running time. It describes the best-case scenario for the algorithm's growth rate.

- **Average-Case:** The expected time an algorithm will take for a typical input. This can be harder to calculate accurately. Represents the **tight bound** of an algorithm's running time. It describes when the best-case and worst-case growth rates are the same, giving a more precise estimate of the algorithm's performance.

```
whenever an interviewer asks for the time complexity of a particular program, they are usually looking for the worst-case scenario, expressed using Big O notation.
```

---
### **Big O Notation (O)** 

This is the most common notation used to express time complexity. It describes the **upper bound** of an algorithm's growth rate, focusing on the dominant term. It essentially tells you "at most, how many operations will this algorithm perform as the input grows very large?".

**[[Common Big O Notations and Examples]]**

1. **Linear Equation**: `y=mx+c or ax+b+c=0`. This represents linear growth, where the time increases proportionally to the input size.
2. .**Quadratic Equation**: `ax2+bx+c=0`. This indicates quadratic growth, where the time increases with the square of the input size.
3.  **Cubic Equation**: `ax3+bx2+cx+d=0`. This shows cubic growth.
4. **Bi Quadratic Equation**: `ax4+bx3+cx2+dx+e=0`. This shows quartic growth.
5. **Logarithmic Equation**: `alog2​n+b`. This represents logarithmic growth, which is very efficient as the time increases slowly with input size.
6. **Exponential Equation**: `y=axb`. This represents exponential growth, which is generally very inefficient for large input sizes

**Order of Big O Notation (Best to Worst):**  Hierarchy of Big O complexities from most efficient ("Best") to least efficient ("Worst")

### ***O(1) < O(logn) < O(n) < O(nlogn) < O(n2) < O(n3) < O(an) < O(n!)***
