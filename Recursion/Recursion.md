
![[Recursion.excalidraw#^group=hJy86imy|100%]]



<div style="border-radius: 12px; padding: 16px; width: 320px; background: linear-gradient(135deg, #f8b195, #f67280, #c06c84); color: #fff; font-family: 'Comic Sans MS', sans-serif; box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2); text-align: center; margin: auto;">
  <h2 style="margin-bottom: 12px; font-size: 1.5em; text-shadow: 2px 2px #333;">📚 Recursion Cheat Sheet</h2>
  <div style="background: rgba(255, 255, 255, 0.2); border-radius: 8px; padding: 12px; margin-bottom: 16px;">
    <h3 style="margin: 0; font-size: 1.2em;">⏱ Time Complexity</h3>
    <p style="margin: 0; font-size: 1em;">No. of calls × Work per call</p>
  </div>
  <div style="background: rgba(255, 255, 255, 0.2); border-radius: 8px; padding: 12px;">
    <h3 style="margin: 0; font-size: 1.2em;">💾 Space Complexity</h3>
    <p style="margin: 0; font-size: 1em;">Height of stack × Memory per call</p>
  </div>
</div>


In a recursive function of the form:

```python
def func():
    if base_case:
        return
    <part1>
    func()  # Recursive call 1
    <part2>
    func()  # Recursive call 2
    <part3>
```

Each part corresponds to specific **operations** or effects on the recursion tree. Here's what they typically represent:

---

### **1. `<part1>` (Pre-recursive operations)**

- **Equivalent Tree Operation**: **Pre-processing the current node**
    - Actions taken **before making recursive calls**. These happen as the function **descends down the recursion tree**.
    - Examples:
        - Initialize or prepare data for the current node.
        - Log or process data before moving to child nodes.
        - Set up state variables or temporary computations.

---

### **2. `func()` (First Recursive Call)**

- **Equivalent Tree Operation**: **Move to the first child of the current node**
    - This call creates a **branch** leading to the first child node in the recursion tree.
    - The subtree rooted at this child node represents the function's execution initiated by this recursive call.

---

### **3. `<part2>` (Between recursive calls)**

- **Equivalent Tree Operation**: **Process after the first child and before the second child**
    - Operations that take place **after returning from the first child** but **before branching to the second child**. Think of it as a **middle step** in processing.
    - Examples:
        - Collect results from the first child.
        - Combine or aggregate data from one branch.
        - Set up data needed for the next recursive call.

---

### **4. `func()` (Second Recursive Call)**

- **Equivalent Tree Operation**: **Move to the second child of the current node**
    - This call creates another branch, leading to the second child node in the recursion tree.
    - The subtree rooted at this child node corresponds to the execution of the second recursive call.

---

### **5. `<part3>` (Post-recursive operations)**

- **Equivalent Tree Operation**: **Post-process the current node**
    - Actions performed **after returning from all recursive calls**, i.e., once both subtrees (or branches) are fully processed.
    - This represents **backtracking** or combining results as the recursion **unwinds** up the tree.
    - Examples:
        - Merge results from left and right subtrees.
        - Clean up temporary data or finalize results.
        - Log information or modify the global state.

---

### **Summary of Tree Analogy**

|Code Part|Equivalent in Recursion Tree|Typical Role|
|---|---|---|
|`<part1>`|Pre-processing of the current node|Prepare the node for further processing.|
|`func()` (1st)|First child branch|Explore the left subtree or first branch.|
|`<part2>`|Transition step between branches|Combine results or prepare for next call.|
|`func()` (2nd)|Second child branch|Explore the right subtree or second branch.|
|`<part3>`|Post-processing of the current node|Aggregate results and finalize processing.|

---

### **Concrete Example**

#### Problem: **Binary Tree Traversal**

```python
def traverse(node):
    if not node:
        return
    print(f"Pre-process: {node.value}")  # Part 1
    traverse(node.left)                 # Recursive call 1
    print(f"Between calls: {node.value}")  # Part 2
    traverse(node.right)                # Recursive call 2
    print(f"Post-process: {node.value}")  # Part 3
```

#### Equivalent Tree Operations:

1. **Pre-process**: Visit the current node (before exploring children).
2. **Recursive call 1**: Explore the left subtree.
3. **Between calls**: Process after the left child, prepare for the right.
4. **Recursive call 2**: Explore the right subtree.
5. **Post-process**: Aggregate results from both subtrees.

---

### **Insights for Problem Solving**

1. **Pre-recursive work**:
    
    - Good for preparing state or accumulating results as you descend the tree.
2. **Between recursive calls**:
    
    - Useful for combining partial results, like summing values from different branches or finding minimums/maximums.
3. **Post-recursive work**:
    
    - Best for tasks that require both subtrees' results, like merging data, returning final values, or reconstructing a structure.

By understanding this structure, you can better **design recursive solutions** and debug their behavior within the recursion tree.

---

## What each node should represent in a recursion tree?

Your confusion is valid! Recursion trees often appear in problem-solving and algorithms as a way to visualize the recursive process. What the **nodes** represent in the recursion tree depends on the specific problem, but there are common conventions and best practices to follow. Let’s clarify:

---

### **What Nodes Typically Represent in Recursion Trees**

A node in a recursion tree **usually represents the current state of the recursive function**, which can include:

1. **The state of input parameters**:
    
    - This is the most common representation.
    - Each node shows the values of the parameters that the recursive function is called with at that level.
    - Example: For a recursive function solving a subset-sum problem, the node might include the remaining sum and the current subset.
2. **The depth of recursion**:
    
    - Sometimes nodes are annotated with their depth in the recursion tree.
    - The depth can indicate the progress of the recursion or the level of recursion for analysis.
3. **The intermediate result (if relevant)**:
    
    - In some problems, nodes may show intermediate results calculated so far.
    - Example: If you’re solving a problem involving combining results from left and right subtrees, the node might show a partial sum or the combined result at that level.
4. **The decision at that step**:
    
    - Particularly useful in backtracking or decision-tree problems.
    - Each node represents a choice made at that recursion level (e.g., "Include this item" or "Skip this item").
5. **Function return values**:
    
    - When analyzing the recursive process, you might label nodes with the value they return to their parent. This is helpful for understanding how solutions propagate back up the tree.

---

### **What to Generally Represent in a Recursion Tree**

For most solutions, include the following:

1. **Input Parameters**:
    
    - These define the "state" of the recursion.
    - Example: If you are calculating Fibonacci numbers, the input parameter could be the current number `n`.
2. **Current Decision (if any)**:
    
    - Useful for problems like subset generation, combinatorics, or backtracking.
    - Example: In the N-Queens problem, the node could indicate the placement of a queen in a column.
3. **Return Value**:
    
    - Represent what value this recursive call returns to its parent.
4. **Depth** (Optional):
    
    - Useful for understanding recursion termination or when you want to compare time complexity.

---

### **Example 1: Fibonacci Sequence**

#### Recursive Function:

```python
def fib(n):
    if n <= 1:
        return n
    return fib(n - 1) + fib(n - 2)
```

#### Recursion Tree for `fib(4)`:

Each node represents the **input parameter** `n` and the **return value**:

```
                 fib(4)
               /       \
           fib(3)       fib(2)
          /    \       /     \
     fib(2)   fib(1) fib(1)  fib(0)
    /    \
fib(1)  fib(0)
```

- **Nodes Represent**: The current input (`n`) and, implicitly, the return value at that level.

---

### **Example 2: Subset Sum Problem**

#### Problem:

Find subsets of a set `S = [1, 2, 3]` that sum to a target.

#### Recursive Function:

```python
def subset_sum(index, target, subset):
    if target == 0:
        print(subset)  # Found a valid subset
        return
    if index >= len(S) or target < 0:
        return
    # Include current element
    subset_sum(index + 1, target - S[index], subset + [S[index]])
    # Exclude current element
    subset_sum(index + 1, target, subset)
```

#### Recursion Tree for `subset_sum(0, 3, [])`:

Each node represents the **current index, target, and subset**:

```
                    (0, 3, [])
                /                  \
        (1, 2, [1])            (1, 3, [])
       /       \              /       \
 (2, 0, [1, 2]) (2, 2, [1]) (2, 1, [2]) (2, 3, [])
```

- **Nodes Represent**:
    1. Current index (`index`).
    2. Remaining target (`target`).
    3. Subset so far (`subset`).

---

### **General Rules for Building a Recursion Tree**

1. **Decide what you want to track**:
    
    - For most problems, track **input parameters** and **return values**.
    - For decision-based problems, track the **current choices**.
2. **Label nodes clearly**:
    
    - Include enough detail in each node to understand the recursion's flow.
3. **Include transitions between nodes**:
    
    - Use arrows to show recursive calls.
    - Annotate arrows with decisions or steps (if helpful).
4. **Track base cases explicitly**:
    
    - Show how recursion terminates at specific nodes (e.g., base cases).

---

### **What Recursion Trees Help With**

1. **Visualizing Recursive Flow**:
    - Understand how calls are made and results propagate back.
2. **Debugging Recursive Functions**:
    - Identify redundant calls, infinite recursion, or incorrect logic.
3. **Time Complexity Analysis**:
    - Use the tree to count the number of nodes (calls) to estimate the function's complexity.

---

### **Key Insight**

A recursion tree is **a tool to model the recursive function's behavior**, and its nodes should reflect **states or values relevant to understanding that behavior**. What you choose to track depends on the problem—parameters, decisions, or return values—but always aim for clarity in what each node represents.