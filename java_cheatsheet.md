# Java Cheatsheet for Coding Interviews

## Variables
```java
// Variables must be declared with types
int n = 0;
System.out.println("n = " + n);
// >>> n = 0

// Cannot change variable type after declaration
String s = "abc";
System.out.println("s = " + s);
// >>> s = abc

// Multiple declarations (but not multiple assignments in one line)
int n = 0;
String m = "abc";
double d = 0.125;
boolean z = false;

// Increment
n = n + 1; // good
n += 1;    // good
n++;       // good (unlike Python)

// null is equivalent to Python's None
Integer num = 4;
num = null;
System.out.println("num = " + num);
// >>> num = null
```

## If-statements
```java
// If statements need parentheses and curly braces
int n = 1;
if (n > 2) {
    n -= 1;
} else if (n == 2) {
    n *= 2;
} else {
    n += 2;
}

// Multi-line conditions need parentheses
// && = and
// || = or
int n = 1, m = 2;
if ((n > 2 && 
    n != m) || n == m) {
    n += 1;
}
```

## Loops
```java
int n = 5;
while (n < 5) {
    System.out.println(n);
    n++;
}

// Looping from i = 0 to i = 4
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}

// Looping from i = 2 to i = 5
for (int i = 2; i <= 5; i++) {
    System.out.println(i);
}

// Looping from i = 5 to i = 2
for (int i = 5; i > 1; i--) {
    System.out.println(i);
}

// Enhanced for loop (for arrays and collections)
int[] nums = {1, 2, 3};
for (int num : nums) {
    System.out.println(num);
}
```

## Math
```java
// Division of integers gives integer result (truncated)
System.out.println(5 / 2); // 2

// To get decimal division, one operand must be a decimal
System.out.println(5 / 2.0); // 2.5

// Integer division always rounds toward zero
System.out.println(-3 / 2); // -1

// Modulo is similar to most languages
System.out.println(10 % 3); // 1

// Negative values in modulo follow the sign of the dividend
System.out.println(-10 % 3); // -1

// Math helpers
System.out.println(Math.floor(3.0 / 2)); // 1.0
System.out.println(Math.ceil(3.0 / 2));  // 2.0
System.out.println(Math.sqrt(2));        // 1.4142135623730951
System.out.println(Math.pow(2, 3));      // 8.0

// Max / Min values
Integer.MAX_VALUE;  // 2^31 - 1
Integer.MIN_VALUE;  // -2^31
Double.POSITIVE_INFINITY;
Double.NEGATIVE_INFINITY;

// Watch out for integer overflow
System.out.println(Integer.MAX_VALUE + 1); // Negative number! (overflow)

// For big integers, use BigInteger
import java.math.BigInteger;
BigInteger big = new BigInteger("2").pow(200);
System.out.println(big); // 1606938044258990275541962092341162602522202993782792835301376
```

## Arrays
```java
// Arrays need to have their size defined and are fixed length
int[] arr = {1, 2, 3};
System.out.println(Arrays.toString(arr)); // [1, 2, 3]

// Cannot use push/pop like in Python
// Use ArrayList for dynamic arrays
ArrayList<Integer> list = new ArrayList<>();
list.add(4);
list.add(5);
System.out.println(list); // [4, 5]

list.remove(list.size() - 1); // Remove last element (like pop)
System.out.println(list); // [4]

list.add(1, 7); // Insert 7 at index 1
System.out.println(list); // [4, 7]

list.set(0, 0); // Set element at index 0 to 0
System.out.println(list); // [0, 7]

// Initialize array of size n with default value 0
int n = 5;
int[] arr = new int[n]; // All elements are 0 by default
System.out.println(Arrays.toString(arr)); // [0, 0, 0, 0, 0]
System.out.println(arr.length); // 5

// Initialize with non-zero values
int[] arr = new int[n];
Arrays.fill(arr, 1);
System.out.println(Arrays.toString(arr)); // [1, 1, 1, 1, 1]

// No negative indexing like in Python
// Use arr[arr.length - 1] instead of arr[-1]
int[] arr = {1, 2, 3};
System.out.println(arr[arr.length - 1]); // 3

// Subarrays using Arrays.copyOfRange
int[] arr = {1, 2, 3, 4};
int[] subArr = Arrays.copyOfRange(arr, 1, 3); // From index 1 (inclusive) to 3 (exclusive)
System.out.println(Arrays.toString(subArr)); // [2, 3]

// Loop through arrays
int[] nums = {1, 2, 3};

// Using index
for (int i = 0; i < nums.length; i++) {
    System.out.println(nums[i]);
}

// Without index (enhanced for loop)
for (int n : nums) {
    System.out.println(n);
}

// With index and value (more verbose in Java)
for (int i = 0; i < nums.length; i++) {
    System.out.println(i + " " + nums[i]);
}

// Sorting
int[] arr = {5, 4, 7, 3, 8};
Arrays.sort(arr);
System.out.println(Arrays.toString(arr)); // [3, 4, 5, 7, 8]

// Sort in descending order (requires more code)
Integer[] arr = {5, 4, 7, 3, 8};
Arrays.sort(arr, Collections.reverseOrder());
System.out.println(Arrays.toString(arr)); // [8, 7, 5, 4, 3]

// Sort array of objects with custom comparator
String[] arr = {"bob", "alice", "jane", "doe"};
Arrays.sort(arr);
System.out.println(Arrays.toString(arr)); // [alice, bob, doe, jane]

// Custom sort (by length of string)
Arrays.sort(arr, Comparator.comparing(String::length));
System.out.println(Arrays.toString(arr)); // [bob, doe, jane, alice]

// 2-D arrays
int[][] arr = new int[4][4];
for (int i = 0; i < arr.length; i++) {
    for (int j = 0; j < arr[i].length; j++) {
        arr[i][j] = 0;
    }
}
System.out.println(arr[0][0] + " " + arr[3][3]); // 0 0
```

## Strings
```java
// Strings are similar to arrays but immutable
String s = "abc";
System.out.println(s.substring(0, 2)); // ab

// Cannot modify individual characters
// s.charAt(0) = 'A'; // Error

// String concatenation
s += "def";
System.out.println(s); // abcdef

// String to number conversion
System.out.println(Integer.parseInt("123") + Integer.parseInt("123")); // 246

// Number to string conversion
System.out.println("" + 123 + 123); // 123123
// or
System.out.println(String.valueOf(123) + String.valueOf(123)); // 123123

// Get ASCII value of a character
System.out.println((int)'a'); // 97
System.out.println((int)'b'); // 98

// Character to string conversion
char c = 'a';
String s = Character.toString(c);

// Join array of strings
String[] strings = {"ab", "cd", "ef"};
System.out.println(String.join("", strings)); // abcdef
```

## Queues
```java
// Queue interface
Queue<Integer> queue = new LinkedList<>();
queue.add(1);
queue.add(2);
System.out.println(queue); // [1, 2]

queue.poll(); // Removes and returns the head
System.out.println(queue); // [2]

// Deque for double-ended queue operations
Deque<Integer> deque = new LinkedList<>();
deque.addLast(1);
deque.addLast(2);
System.out.println(deque); // [1, 2]

deque.pollFirst(); // Removes from front
System.out.println(deque); // [2]

deque.addFirst(1); // Add to front
System.out.println(deque); // [1, 2]

deque.pollLast(); // Removes from end
System.out.println(deque); // [1]
```

## HashSets
```java
// HashSet (no duplicates)
HashSet<Integer> set = new HashSet<>();

set.add(1);
set.add(2);
System.out.println(set); // [1, 2]
System.out.println(set.size()); // 2

System.out.println(set.contains(1)); // true
System.out.println(set.contains(2)); // true
System.out.println(set.contains(3)); // false

set.remove(2);
System.out.println(set.contains(2)); // false

// Array to set
Integer[] nums = {1, 2, 3};
HashSet<Integer> numSet = new HashSet<>(Arrays.asList(nums));
System.out.println(numSet); // [1, 2, 3]
```

## HashMaps
```java
// HashMap (dictionary in Python)
HashMap<String, Integer> map = new HashMap<>();
map.put("alice", 88);
map.put("bob", 77);
System.out.println(map); // {bob=77, alice=88}
System.out.println(map.size()); // 2

map.put("alice", 80); // Update value
System.out.println(map.get("alice")); // 80

System.out.println(map.containsKey("alice")); // true
map.remove("alice");
System.out.println(map.containsKey("alice")); // false

// Initialize with values
Map<String, Integer> map = Map.of("alice", 90, "bob", 70);
System.out.println(map); // {bob=70, alice=90}

// Looping through maps
HashMap<String, Integer> map = new HashMap<>();
map.put("alice", 90);
map.put("bob", 70);

// Loop through keys
for (String key : map.keySet()) {
    System.out.println(key + " " + map.get(key));
}

// Loop through values
for (Integer val : map.values()) {
    System.out.println(val);
}

// Loop through entries
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    System.out.println(entry.getKey() + " " + entry.getValue());
}
```

## Heap / Priority Queue
```java
// Min heap (Priority Queue)
PriorityQueue<Integer> minHeap = new PriorityQueue<>();
minHeap.add(3);
minHeap.add(2);
minHeap.add(4);

// Peek at minimum value
System.out.println(minHeap.peek()); // 2

// Poll removes and returns minimum value
while (!minHeap.isEmpty()) {
    System.out.println(minHeap.poll());
}
// Output: 2, 3, 4

// Max heap (needs a comparator)
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
maxHeap.add(3);
maxHeap.add(2);
maxHeap.add(4);

System.out.println(maxHeap.peek()); // 4

while (!maxHeap.isEmpty()) {
    System.out.println(maxHeap.poll());
}
// Output: 4, 3, 2

// Initialize with values
Integer[] nums = {2, 1, 8, 4, 5};
PriorityQueue<Integer> heap = new PriorityQueue<>(Arrays.asList(nums));
while (!heap.isEmpty()) {
    System.out.println(heap.poll());
}
// Output: 1, 2, 4, 5, 8
```

## Functions/Methods
```java
public static int myFunc(int n, int m) {
    return n * m;
}

System.out.println(myFunc(3, 4)); // 12

// Java doesn't have nested functions like Python
// But can use inner classes or lambda expressions
public static String outer(String a, String b) {
    String c = "c";
    
    // Using a lambda or anonymous inner class
    Function<Void, String> inner = (Void) -> {
        return a + b + c;
    };
    
    return inner.apply(null);
}

System.out.println(outer("a", "b")); // abc

// Pass by value for primitives, pass by reference for objects
public static void doubleArray(int[] arr, Integer val) {
    // Modifying array works (pass by reference)
    for (int i = 0; i < arr.length; i++) {
        arr[i] *= 2;
    }
    
    // This will only modify the local copy of val (pass by value)
    val *= 2;
}

int[] nums = {1, 2};
Integer val = 3;
doubleArray(nums, val);
System.out.println(Arrays.toString(nums) + " " + val); // [2, 4] 3
```

## Classes
```java
class MyClass {
    // Member variables
    private int[] nums;
    private int size;
    
    // Constructor
    public MyClass(int[] nums) {
        this.nums = nums;
        this.size = nums.length;
    }
    
    // Method
    public int getLength() {
        return this.size;
    }
    
    public int getDoubleLength() {
        return 2 * this.getLength();
    }
}

MyClass myObj = new MyClass(new int[]{1, 2, 3});
System.out.println(myObj.getLength());       // 3
System.out.println(myObj.getDoubleLength()); // 6
```