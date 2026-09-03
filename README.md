# Exp-11-IMPLEMENTATION-OF-HUFFMAN-CODING
## Date: 03/09/2026
## Name: T.GOSHANRAJAN
## Register No.: 212225040098
## Aim
To implement Huffman coding to compress the data using Python.

## Software Required
Anaconda - Python 3.7
## Algorithm:
### Step 1: 
Read the input string and calculate the frequency of occurrence of each character.

### Step 2: 
Create a node for each character and store its frequency. Insert all the nodes into a priority queue based on their frequency.

### Step 3:
Remove the two nodes with the lowest frequencies from the priority queue and create a new node by combining their frequencies. Insert the new node back into the priority queue.

### Step 4: 
Repeat Step 3 until only one node remains. This node becomes the root of the Huffman tree.

### Step 5: 
Traverse the Huffman tree and assign 0 to the left branch and 1 to the right branch. The resulting binary sequence for each character is its Huffman code. Use these codes to encode and compress the input data.

## Program:

```
# Step 1: Get the input string
input_string = "huffman coding"  # Example input string
```
```
# Step 2: Calculate frequency of each character in the input string
frequency = {}
for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1
```
```
# Step 3: Create tree nodes
nodes = [[char, freq] for char, freq in frequency.items()]
```
```
# Step 4: Main function to implement Huffman coding
while len(nodes) > 1:
    # Sort nodes based on frequency
    nodes = sorted(nodes, key=lambda x: x[1])
​
    # Pick two smallest nodes
    left = nodes.pop(0)
    right = nodes.pop(0)
​
    # Create a new node with combined frequency
    new_node = [[left, right], left[1] + right[1]]
    nodes.append(new_node)
​
# The final node is the Huffman tree
huffman_tree = nodes[0]
```
```
# Step 5: Generate Huffman codes
huffman_codes = {}
​
def generate_codes(tree, code=""):
    if isinstance(tree[0], str):  # If it's a leaf node
        huffman_codes[tree[0]] = code
    else:  # If it's an internal node, recurse
        generate_codes(tree[0][0], code + "0")
        generate_codes(tree[0][1], code + "1")
​
generate_codes(huffman_tree)
```
```
# Step 6: Print the characters and their Huffman codes
print("Character | Huffman Code")
print("-------------------------")
for char, code in huffman_codes.items():
    print(f"    {char}    |    {code}")
​
```

## Output:

<img width="497" height="372" alt="image" src="https://github.com/user-attachments/assets/a180f2e4-1d19-4382-85c3-48831edeefad" />



## Result
Thus the huffman coding was implemented to compress the data using python programming.
