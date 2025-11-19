[chat gpt chat link](https://chatgpt.com/share/691e37fe-503c-8003-873e-2da04350a829)


# Lists:
In python lists are actually dynamic arrays whose elements are stored contiguously in memory (uninterrupted blocks of memory addresses), they have O(1) access due to being accessed by index.

When a list runs out of space, python allocates a bigger chunk of memory and copies all elements of the list into the newly allocated memory. This is an expensive O(n) operation, but it does't happen very often, so appending an element to a list has an amortized O(1) time complexity.

Inserting and removing elements from the middle or start of the list, is O(n) because it requires displacing other elements on the list. If you remove the first element, all other elements need to be shifted one index to the left.

Searching is a linear operation, so it's O(n)

# Dictionaries
In python dictionaries are actually hash tables, they are a key, value data structure.
The key is feed to a hashing function whose output indicate the memory address where the value should be stored. Dictionaries are accessed by key and have an average O(1) time complexity for reads writes and deletions. It can occur however that two different keys map to the same memory address, this is what we call a collision. Collisions degrade the performance of dictionaries, and in a worst case scenario, the performance for all operations becomes O(n), this is a scenario where the dictionary is behaving like a linked list due to an excessive number of collisions.

# Stacks:
A Stack is a **LIFO** data structure, that is, a data structure where the last element to be inserted is the first one to be retrieved. LIFO stands for Last In First Out.

Python has no built in implementation of the stack data structure, but this can be done using a `list`or an instance of `collections.deque`

# Queue
A Queue is a **FIFO** data structure, that is, a data structure where the first element to be inserted is also the first element to be retrieved. FIFO stands for first in first out.

Given that when using a queue we are constantly removing the first element, it is not a good idea to implement a queue with a list, due to the shifting of elements.

For queues Python provides the built in `collections.deque`, a double ended queue with method such as `append`, `appendleft` `pop` and `popleft` all of which have an O(1) time complexity.



