/////////////////Q1. Write a program to implement the following operations on a 1D array: i. Insert an element at a specific position. ii. Delete an element from a specific position. iii. Search for an element in the array.
//////////////////
Ans: import java.util.Scanner;
public class ArrayOperations {
// Method to insert an element at a specific position
public static int[] insertElement(int[] array, int element, int position) {
// If position is out of bounds, return the array as is
if (position < 0 || position > array.length) {
System.out.println("Invalid position!");
return array;
}
// Create a new array with one extra space
int[] newArray = new int[array.length + 1];
// Copy elements before the insertion position
for (int i = 0; i < position; i++) {
newArray[i] = array[i];
}
// Insert the new element at the specified position
newArray[position] = element;
// Copy elements after the insertion position
for (int i = position; i < array.length; i++) {
newArray[i + 1] = array[i];
}
return newArray;
}
// Method to delete an element at a specific position
public static int[] deleteElement(int[] array, int position) {
// If position is out of bounds, return the array as is
if (position < 0 || position >= array.length) {
System.out.println("Invalid position!");
return array; }
// Create a new array with one less space
int[] newArray = new int[array.length - 1];
// Copy elements before the deletion position
for (int i = 0; i < position; i++) {
newArray[i] = array[i];
}
// Copy elements after the deletion position
for (int i = position + 1; i < array.length; i++) {
newArray[i - 1] = array[i];
}
return newArray;
}
// Method to search for an element in the array
public static boolean searchElement(int[] array, int element) {
for (int i = 0; i < array.length; i++) {
if (array[i] == element) {
return true; // Element found
}
}
return false; // Element not found
}
// Method to display the array
public static void displayArray(int[] array) {
for (int i = 0; i < array.length; i++) {
System.out.print(array[i] + " ");
}
System.out.println();
}
public static void main(String[] args) {
Scanner scanner = new Scanner(System.in);
// Sample array for demonstration
int[] array = {10, 20, 30, 40, 50};
while (true) {
System.out.println("Select an operation:");
System.out.println("1. Insert an element");
System.out.println("2. Delete an element");
System.out.println("3. Search for an element");
System.out.println("4. Display the array");
System.out.println("5. Exit");
int choice = scanner.nextInt();
switch (choice) {
case 1: // Insert an element
System.out.print("Enter the element to insert: ");
int insertElement = scanner.nextInt();
System.out.print("Enter the position to insert the element: ");
int insertPosition = scanner.nextInt();
array = insertElement(array, insertElement, insertPosition);
break;
case 2: // Delete an element
System.out.print("Enter the position to delete the element from: ");
int deletePosition = scanner.nextInt();
array = deleteElement(array, deletePosition);
break;
case 3: // Search for an element
System.out.print("Enter the element to search: ");
int searchElement = scanner.nextInt();
if (searchElement(array, searchElement)) {
System.out.println("Element found in the array.");
} else {
System.out.println("Element not found.");
}
break;
case 4: // Display the array
System.out.print("Current array: ");
displayArray(array);
break;
case 5: // Exit
System.out.println("Exiting program.");
scanner.close();
return;
default:
System.out.println("Invalid choice. Please try again.");
}
}
}
}
///////////////////////////////////////////////////////////////////////////////////////////////////////
Q2. Write a program to perform matrix operations (addition, subtraction, multiplication) using 2D arrays.
import java.util.Scanner;
public class MatrixOperations {
// Method to add two matrices
public static int[][] addMatrices(int[][] matrix1, int[][] matrix2) {
int rows = matrix1.length;
int cols = matrix1[0].length;
// Create a new matrix for the result
int[][] result = new int[rows][cols];
// Add corresponding elements of the matrices
for (int i = 0; i < rows; i++) {
for (int j = 0; j < cols; j++) {
result[i][j] = matrix1[i][j] + matrix2[i][j];
}
}
return result;
}
// Method to subtract two matrices
public static int[][] subtractMatrices(int[][] matrix1, int[][] matrix2) {
int rows = matrix1.length;
int cols = matrix1[0].length;
// Create a new matrix for the result
int[][] result = new int[rows][cols];
// Subtract corresponding elements of the matrices
for (int i = 0; i < rows; i++) {
for (int j = 0; j < cols; j++) {
result[i][j] = matrix1[i][j] - matrix2[i][j];
}
}
return result;
}
// Method to multiply two matrices
public static int[][] multiplyMatrices(int[][] matrix1, int[][] matrix2) {
int rows1 = matrix1.length;
int cols1 = matrix1[0].length;
int rows2 = matrix2.length;
int cols2 = matrix2[0].length;
// Check if multiplication is possible (cols1 == rows2)
if (cols1 != rows2) {
System.out.println("Matrix multiplication is not possible: number of columns in matrix1 must equal number of rows in matrix2.");
return new int[0][0];
}
// Create a new matrix for the result
int[][] result = new int[rows1][cols2];
// Multiply the matrices
for (int i = 0; i < rows1; i++) {
for (int j = 0; j < cols2; j++) {
for (int k = 0; k < cols1; k++) {
result[i][j] += matrix1[i][k] * matrix2[k][j];
}
}
}
return result;
}
//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
Q3. : Implement a singly linked list with the following operations:
i.
Insert a node at the beginning, middle, and end.
ii.
Delete a node from a given position.
iii.
Search for an element in the linked list.
import java.util.Scanner;
public class SinglyLinkedList {
// Node class to represent each element in the list
static class Node {
int data;
Node next;
// Constructor
Node(int data) {
this.data = data;
this.next = null;
}
}
// Head of the list
private Node head;
// Constructor
public SinglyLinkedList() {
this.head = null;
}
// Method to insert a node at the beginning
public void insertAtBeginning(int data) {
Node newNode = new Node(data);
newNode.next = head; // Make new node point to the old head
head = newNode; // Update head to the new node
}
// Method to insert a node at the end
public void insertAtEnd(int data) {
Node newNode = new Node(data);
if (head == null) {
head = newNode; // If list is empty, new node becomes the head
return;
}
Node current = head;
while (current.next != null) {
current = current.next; // Traverse to the last node
}
current.next = newNode; // Make the last node point to the new node
}
// Method to insert a node at a specific position (middle or any position)
public void insertAtPosition(int data, int position) {
if (position < 1) {
System.out.println("Invalid position!");
return;
}
Node newNode = new Node(data);
// If inserting at the beginning
if (position == 1) {
newNode.next = head;
head = newNode;
return;
}
// Traverse the list to find the position
Node current = head;
for (int i = 1; i < position - 1; i++) {
if (current == null) {
System.out.println("Position out of range.");
return;
}
current = current.next;
}
// Insert the new node at the specified position
newNode.next = current.next;
current.next = newNode;
}
// Method to delete a node from a given position
public void deleteAtPosition(int position) {
if (head == null || position < 1) {
System.out.println("Invalid position or empty list!");
return;
}
// If deleting the first node
if (position == 1) {
head = head.next;
return;
}
Node current = head;
for (int i = 1; i < position - 1; i++) {
if (current == null || current.next == null) {
System.out.println("Position out of range.");
return;
}
current = current.next;
}
// Delete the node at the given position
if (current.next == null) {
System.out.println("Position out of range.");
return;
}
current.next = current.next.next;
}
// Method to search for an element in the list
public boolean search(int data) {
Node current = head;
while (current != null) {
if (current.data == data) {
return true;
}
current = current.next;
}
return false;
}
// Method to display the linked list
public void display() {
if (head == null) {
System.out.println("The list is empty.");
return;
}
Node current = head;
while (current != null) {
System.out.print(current.data + " -> ");
current = current.next;
}
System.out.println("null");
}
public static void main(String[] args) {
Scanner scanner = new Scanner(System.in);
SinglyLinkedList list = new SinglyLinkedList();
while (true) {
System.out.println("\nSelect an operation:");
System.out.println("1. Insert at beginning");
System.out.println("2. Insert at end");
System.out.println("3. Insert at a specific position");
System.out.println("4. Delete a node from a given position");
System.out.println("5. Search for an element");
System.out.println("6. Display the list");
System.out.println("7. Exit");
System.out.print("Enter your choice: ");
int choice = scanner.nextInt();
switch (choice) {
case 1:
System.out.print("Enter the value to insert at the beginning: ");
int data1 = scanner.nextInt();
list.insertAtBeginning(data1);
break;
case 2:
System.out.print("Enter the value to insert at the end: ");
int data2 = scanner.nextInt();
list.insertAtEnd(data2);
break;
case 3:
System.out.print("Enter the value to insert: ");
int data3 = scanner.nextInt();
System.out.print("Enter the position to insert the value at: ");
int position3 = scanner.nextInt();
list.insertAtPosition(data3, position3);
break;
case 4:
System.out.print("Enter the position to delete the node from: ");
int position4 = scanner.nextInt();
list.deleteAtPosition(position4);
break;
case 5:
System.out.print("Enter the value to search for: ");
int data5 = scanner.nextInt();
if (list.search(data5)) {
System.out.println("Element found in the list.");
} else {
System.out.println("Element not found.");
}
break;
case 6:
System.out.println("Current list:");
list.display();
break;
case 7:
System.out.println("Exiting program.");
scanner.close();
return;
default:
System.out.println("Invalid choice! Please try again.");
}
}
}
}

//////////////////////////////////////////////////////////////////////////////////////////////////////////
Q4. : Implement a doubly linked list with the following operations:
i.
Insert a node at the beginning and end.
ii.
Delete a node from the beginning and end.
iii.
Reverse the doubly linked list.
import java.util.Scanner;
public class DoublyLinkedList {
// Node class for a doubly linked list
static class Node {
int data;
Node next;
Node prev;
// Constructor to create a new node
Node(int data) {
this.data = data;
this.next = null;
this.prev = null;
}
}
private Node head;
// Constructor to initialize the doubly linked list
public DoublyLinkedList() {
head = null;
}
// Method to insert a node at the beginning
public void insertAtBeginning(int data) {
Node newNode = new Node(data);
if (head == null) {
head = newNode; // If list is empty, new node is the head
} else {
newNode.next = head; // Make the new node point to the current head
head.prev = newNode; // Make the old head point back to the new node
head = newNode; // Update the head to be the new node
}
}
// Method to insert a node at the end
public void insertAtEnd(int data) {
Node newNode = new Node(data);
if (head == null) {
head = newNode; // If the list is empty, new node becomes the head
return;
}
Node last = head;
while (last.next != null) {
last = last.next; // Traverse to the last node
}
last.next = newNode; // Link the last node to the new node
newNode.prev = last; // Make the new node's prev point to the last node
}
// Method to delete a node from the beginning
public void deleteFromBeginning() {
if (head == null) {
System.out.println("The list is empty!");
return;
}
if (head.next == null) {
head = null; // If there's only one node, make head null
} else {
head = head.next; // Move head to the next node
head.prev = null; // Make the new head's prev null
}
}
// Method to delete a node from the end
public void deleteFromEnd() {
if (head == null) {
System.out.println("The list is empty!");
return;
}
if (head.next == null) {
head = null; // If there's only one node, make head null
} else {
Node last = head;
while (last.next != null) {
last = last.next; // Traverse to the last node
}
last.prev.next = null; // Remove the last node by making the previous node's next null
}
}
// Method to reverse the doubly linked list
public void reverse() {
if (head == null) {
System.out.println("The list is empty!");
return;
}
Node temp = null;
Node current = head;
// Swap the next and prev pointers for each node
while (current != null) {
temp = current.prev;
current.prev = current.next;
current.next = temp;
current = current.prev; // Move to the next node (which was the previous node before swap)
}
if (temp != null) {
head = temp.prev; // Update head to be the new head (previously the last node)
}
}
// Method to display the list from beginning to end
public void display() {
if (head == null) {
System.out.println("The list is empty.");
return;
}
Node current = head;
while (current != null) {
System.out.print(current.data + " <-> ");
current = current.next;
}
System.out.println("null");
}
public static void main(String[] args) {
Scanner scanner = new Scanner(System.in);
DoublyLinkedList list = new DoublyLinkedList();
while (true) {
System.out.println("\nSelect an operation:");
System.out.println("1. Insert at the beginning");
System.out.println("2. Insert at the end");
System.out.println("3. Delete from the beginning");
System.out.println("4. Delete from the end");
System.out.println("5. Reverse the list");
System.out.println("6. Display the list");
System.out.println("7. Exit");
System.out.print("Enter your choice: ");
int choice = scanner.nextInt();
switch (choice) {
case 1:
System.out.print("Enter the value to insert at the beginning: ");
int data1 = scanner.nextInt();
list.insertAtBeginning(data1);
break;
case 2:
System.out.print("Enter the value to insert at the end: ");
int data2 = scanner.nextInt();
list.insertAtEnd(data2);
break;
case 3:
list.deleteFromBeginning();
break;
case 4:
list.deleteFromEnd();
break;
case 5:
list.reverse();
break;
case 6:
System.out.println("Current list:");
list.display();
break;
case 7:
System.out.println("Exiting program.");
scanner.close();
return;
default:
System.out.println("Invalid choice! Please try again.");
}
}
}
}

///////////////////////////////////////////////////////////////////////////////////////////////////////////////
Q5. : Write a program to implement a stack using arrays and linked lists. Perform the following:
i.
Push an element.
ii.
Pop an element.
iii.
Check if the stack is empty.
iv.
Convert an infix expression to postfix and evaluate it.
import java.util.Stack;
import java.util.Scanner;
class StackArray {
private int maxSize;
private int top;
private int[] stack;
public StackArray(int size) {
maxSize = size;
stack = new int[maxSize];
top = -1;
}
// Push operation: Add an element to the stack
public void push(int value) {
if (top == maxSize - 1) {
System.out.println("Stack Overflow! Cannot push.");
} else {
stack[++top] = value;
System.out.println(value + " pushed to stack");
}
}
// Pop operation: Remove an element from the stack
public int pop() {
if (top == -1) {
System.out.println("Stack Underflow! Cannot pop.");
return -1;
} else {
return stack[top--];
}
}
// Check if the stack is empty
public boolean isEmpty() {
return top == -1;
}
}
class StackLinkedList {
private Node top;
// Node class for Linked List implementation
class Node {
int data;
Node next;
public Node(int data) {
this.data = data;
next = null;
}
}
public StackLinkedList() {
top = null;
}
// Push operation: Add an element to the stack
public void push(int value) {
Node newNode = new Node(value);
newNode.next = top;
top = newNode;
System.out.println(value + " pushed to stack");
}
// Pop operation: Remove an element from the stack
public int pop() {
if (top == null) {
System.out.println("Stack Underflow! Cannot pop.");
return -1;
} else {
int poppedValue = top.data;
top = top.next;
return poppedValue;
}
}
// Check if the stack is empty
public boolean isEmpty() {
return top == null;
}
}
public class StackOperations {
// Method to get precedence of operators
public static int precedence(char ch) {
if (ch == '+' || ch == '-') {
return 1;
} else if (ch == '*' || ch == '/') {
return 2;
}
return 0;
}
// Method to convert infix to postfix expression
public static String infixToPostfix(String infix) {
Stack<Character> stack = new Stack<>();
StringBuilder postfix = new StringBuilder();
for (char ch : infix.toCharArray()) {
if (Character.isLetterOrDigit(ch)) {
postfix.append(ch);
} else if (ch == '(') {
stack.push(ch);
} else if (ch == ')') {
while (!stack.isEmpty() && stack.peek() != '(') {
postfix.append(stack.pop());
}
stack.pop(); // Pop the '('
} else { // Operator
while (!stack.isEmpty() && precedence(ch) <= precedence(stack.peek())) {
postfix.append(stack.pop());
}
stack.push(ch);
}
}
// Pop remaining operators from the stack
while (!stack.isEmpty()) {
postfix.append(stack.pop());
}
return postfix.toString();
}
// Method to evaluate postfix expression
public static int evaluatePostfix(String postfix) {
Stack<Integer> stack = new Stack<>();
for (char ch : postfix.toCharArray()) {
if (Character.isDigit(ch)) {
stack.push(ch - '0'); // Convert char to int and push
} else {
int b = stack.pop();
int a = stack.pop();
switch (ch) {
case '+':
stack.push(a + b);
break;
case '-':
stack.push(a - b);
break;
case '*':
stack.push(a * b);
break;
case '/':
stack.push(a / b);
break;
}
}
}
return stack.pop();
}
public static void main(String[] args) {
Scanner scanner = new Scanner(System.in);
// Menu for stack operations (using array or linked list)
System.out.println("Enter the stack type (1: Array, 2: LinkedList): ");
int choice = scanner.nextInt();
if (choice == 1) {
// Using Stack implemented with Array
System.out.print("Enter the size of the stack: ");
int size = scanner.nextInt();
StackArray stackArray = new StackArray(size);
// Perform stack operations
while (true) {
System.out.println("\nSelect an operation:");
System.out.println("1. Push");
System.out.println("2. Pop");
System.out.println("3. Check if stack is empty");
System.out.println("4. Exit");
System.out.print("Enter your choice: ");
int operation = scanner.nextInt();
switch (operation) {
case 1:
System.out.print("Enter value to push: ");
int value = scanner.nextInt();
stackArray.push(value);
break;
case 2:
int poppedValue = stackArray.pop();
if (poppedValue != -1) {
System.out.println("Popped value: " + poppedValue);
}
break;
case 3:
System.out.println("Is stack empty? " + stackArray.isEmpty());
break;
case 4:
System.out.println("Exiting program.");
return;
default:
System.out.println("Invalid choice! Try again.");
}
}
} else if (choice == 2) {
// Using Stack implemented with Linked List
StackLinkedList stackLinkedList = new StackLinkedList();
// Perform stack operations
while (true) {
System.out.println("\nSelect an operation:");
System.out.println("1. Push");
System.out.println("2. Pop");
System.out.println("3. Check if stack is empty");
System.out.println("4. Exit");
System.out.print("Enter your choice: ");
int operation = scanner.nextInt();
switch (operation) {
case 1:
System.out.print("Enter value to push: ");
int value = scanner.nextInt();
stackLinkedList.push(value);
break;
case 2:
int poppedValue = stackLinkedList.pop();
if (poppedValue != -1) {
System.out.println("Popped value: " + poppedValue);
}
break;
case 3:
System.out.println("Is stack empty? " + stackLinkedList.isEmpty());
break;
case 4:
System.out.println("Exiting program.");
return;
default:
System.out.println("Invalid choice! Try again.");
}
}
}
// Evaluate infix to postfix conversion and evaluation
scanner.nextLine(); // Consume the newline
System.out.print("Enter an infix expression (e.g., (A+B)*C): ");
String infix = scanner.nextLine();
String postfix = infixToPostfix(infix);
System.out.println("Postfix expression: " + postfix);
// Example of evaluating postfix expression (Assumes single-digit operands)
int result = evaluatePostfix(postfix);
System.out.println("Result of postfix evaluation: " + result);
}
}

///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
Q6. Write a program to implement a circular queue using an array. Perform the following:
v.
Enqueue an element.
vi.
Dequeue an element.
vii.
Check if the queue is full or empty.
import java.util.Scanner;
class CircularQueue {
private int[] queue;
private int front, rear, size, capacity;
// Constructor to initialize the queue
public CircularQueue(int capacity) {
this.capacity = capacity;
queue = new int[capacity];
front = rear = -1;
size = 0;
}
// Enqueue operation: Add an element to the queue
public void enqueue(int data) {
if (isFull()) {
System.out.println("Queue is full! Cannot enqueue.");
} else {
if (front == -1) {
front = 0; // If the queue is empty, set front to 0
}
rear = (rear + 1) % capacity; // Circular increment
queue[rear] = data;
size++;
System.out.println(data + " enqueued to the queue.");
}
}
// Dequeue operation: Remove an element from the queue
public int dequeue() {
if (isEmpty()) {
System.out.println("Queue is empty! Cannot dequeue.");
return -1; // Return a sentinel value
} else {
int dequeuedValue = queue[front];
if (front == rear) {
front = rear = -1; // If there's only one element, reset the queue
} else {
front = (front + 1) % capacity; // Circular increment
}
size--;
return dequeuedValue;
}
}
// Check if the queue is empty
public boolean isEmpty() {
return size == 0;
}
// Check if the queue is full
public boolean isFull() {
return size == capacity;
}
}
public class CircularQueueDemo {
public static void main(String[] args) {
Scanner scanner = new Scanner(System.in);
// Create a CircularQueue with a specified capacity
System.out.print("Enter the capacity of the queue: ");
int capacity = scanner.nextInt();
CircularQueue queue = new CircularQueue(capacity);
// Menu for performing queue operations
while (true) {
System.out.println("\nSelect an operation:");
System.out.println("1. Enqueue");
System.out.println("2. Dequeue");
System.out.println("3. Check if the queue is empty");
System.out.println("4. Check if the queue is full");
System.out.println("5. Exit");
System.out.print("Enter your choice: ");
int choice = scanner.nextInt();
switch (choice) {
case 1:
System.out.print("Enter the value to enqueue: ");
int value = scanner.nextInt();
queue.enqueue(value);
break;
case 2:
int dequeuedValue = queue.dequeue();
if (dequeuedValue != -1) {
System.out.println(dequeuedValue + " dequeued from the queue.");
}
break;
case 3:
System.out.println("Is the queue empty? " + queue.isEmpty());
break;
case 4:
System.out.println("Is the queue full? " + queue.isFull());
break;
case 5:
System.out.println("Exiting program.");
scanner.close();
return;
default:
System.out.println("Invalid choice! Please try again.");
}
}
}
}

////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
Q7. Implement a binary search tree with the following operations:
i.
Insert a node.
ii.
Delete a node.
iii.
Traverse the tree using in-order, pre-order, and post-order traversals.
// Binary Search Tree implementation
class BinarySearchTree {
// Definition for a Node
class Node {
int data;
Node left, right;
public Node(int data) {
this.data = data;
left = right = null;
}
}
private Node root;
// Constructor to initialize the BST
public BinarySearchTree() {
root = null;
}
// Insert a node into the BST
public void insert(int data) {
root = insertRec(root, data);
}
// Recursive function to insert a node
private Node insertRec(Node root, int data) {
// If the tree is empty, return a new node
if (root == null) {
root = new Node(data);
return root;
}
// Otherwise, recur down the tree
if (data < root.data) {
root.left = insertRec(root.left, data); // Insert in the left subtree
} else if (data > root.data) {
root.right = insertRec(root.right, data); // Insert in the right subtree
}
// Return the (unchanged) node pointer
return root;
}
// Delete a node from the BST
public void delete(int data) {
root = deleteRec(root, data);
}
// Recursive function to delete a node
private Node deleteRec(Node root, int data) {
// Base case: If the tree is empty
if (root == null) {
return root;
}
// Otherwise, recur down the tree
if (data < root.data) {
root.left = deleteRec(root.left, data); // Search in the left subtree
} else if (data > root.data) {
root.right = deleteRec(root.right, data); // Search in the right subtree
} else { // If the node to be deleted is found
// Node with only one child or no child
if (root.left == null) {
return root.right;
} else if (root.right == null) {
return root.left;
}
// Node with two children: Get the inorder successor (smallest in the right subtree)
root.data = minValue(root.right);
// Delete the inorder successor
root.right = deleteRec(root.right, root.data);
}
return root;
}
// Function to get the minimum value (inorder successor)
private int minValue(Node root) {
int minValue = root.data;
while (root.left != null) {
minValue = root.left.data;
root = root.left;
}
return minValue;
}
// In-order traversal (Left, Root, Right)
public void inorder() {
inorderRec(root);
}
private void inorderRec(Node root) {
if (root != null) {
inorderRec(root.left);
System.out.print(root.data + " ");
inorderRec(root.right);
}
}
// Pre-order traversal (Root, Left, Right)
public void preorder() {
preorderRec(root);
}
private void preorderRec(Node root) {
if (root != null) {
System.out.print(root.data + " ");
preorderRec(root.left);
preorderRec(root.right);
}
}
// Post-order traversal (Left, Right, Root)
public void postorder() {
postorderRec(root);
}
private void postorderRec(Node root) {
if (root != null) {
postorderRec(root.left);
postorderRec(root.right);
System.out.print(root.data + " ");
}
}
// Function to check if the tree is empty
public boolean isEmpty() {
return root == null;
}
}
public class BinarySearchTreeDemo {
public static void main(String[] args) {
Scanner scanner = new Scanner(System.in);
// Create a BinarySearchTree object
BinarySearchTree tree = new BinarySearchTree();
// Perform operations
while (true) {
System.out.println("\nSelect an operation:");
System.out.println("1. Insert a node");
System.out.println("2. Delete a node");
System.out.println("3. In-order Traversal");
System.out.println("4. Pre-order Traversal");
System.out.println("5. Post-order Traversal");
System.out.println("6. Check if tree is empty");
System.out.println("7. Exit");
System.out.print("Enter your choice: ");
int choice = scanner.nextInt();
switch (choice) {
case 1:
System.out.print("Enter the value to insert: ");
int insertValue = scanner.nextInt();
tree.insert(insertValue);
break;
case 2:
System.out.print("Enter the value to delete: ");
int deleteValue = scanner.nextInt();
tree.delete(deleteValue);
break;
case 3:
System.out.println("In-order traversal:");
tree.inorder();
System.out.println();
break;
case 4:
System.out.println("Pre-order traversal:");
tree.preorder();
System.out.println();
break;
case 5:
System.out.println("Post-order traversal:");
tree.postorder();
System.out.println();
break;
case 6:
System.out.println("Is the tree empty? " + tree.isEmpty());
break;
case 7:
System.out.println("Exiting program.");
scanner.close();
return;
default:
System.out.println("Invalid choice! Please try again.");
}
}
}
}

/////////////////////////////////////////////////////////////////////////////////////////////////////////
888888888888888888888888888888888888888888888888888888888888888888888888888888888888888888888888888888
Q8. : Write a program to implement an AVL tree. Perform the following:
iii.
Insert nodes and ensure the tree remains balanced.
iv.
Delete a node and perform the necessary rotations to balance the tree.
class AVLTree {
// Definition for a Node in AVL Tree
class Node {
int data;
Node left, right;
int height;
public Node(int data) {
this.data = data;
left = right = null;
height = 1; // Height of the node is initially 1
}
}
private Node root;
// Constructor to initialize the root of the AVL Tree
public AVLTree() {
root = null;
}
// Get the height of the node
private int height(Node node) {
return (node == null) ? 0 : node.height;
}
// Get the balance factor of the node
private int balanceFactor(Node node) {
return (node == null) ? 0 : height(node.left) - height(node.right);
}
// Update the height of the node
private void updateHeight(Node node) {
node.height = 1 + Math.max(height(node.left), height(node.right));
}
// Perform a right rotation
private Node rightRotate(Node y) {
Node x = y.left;
Node T2 = x.right;
// Perform rotation
x.right = y;
y.left = T2;
// Update heights
updateHeight(y);
updateHeight(x);
// Return the new root
return x;
}
// Perform a left rotation
private Node leftRotate(Node x) {
Node y = x.right;
Node T2 = y.left;
// Perform rotation
y.left = x;
x.right = T2;
// Update heights
updateHeight(x);
updateHeight(y);
// Return the new root
return y;
}
// Perform left-right rotation
private Node leftRightRotate(Node node) {
node.left = leftRotate(node.left);
return rightRotate(node);
}
// Perform right-left rotation
private Node rightLeftRotate(Node node) {
node.right = rightRotate(node.right);
return leftRotate(node);
}
// Insert a node into the AVL tree
public void insert(int data) {
root = insertRec(root, data);
}
// Recursive function to insert a node
private Node insertRec(Node node, int data) {
// 1. Perform the normal BST insertion
if (node == null) {
return new Node(data);
}
if (data < node.data) {
node.left = insertRec(node.left, data);
} else if (data > node.data) {
node.right = insertRec(node.right, data);
} else {
return node; // Duplicates are not allowed in the AVL tree
}
// 2. Update the height of the current node
updateHeight(node);
// 3. Get the balance factor and perform rotations if necessary
int balance = balanceFactor(node);
// Left Heavy Case
if (balance > 1 && data < node.left.data) {
return rightRotate(node); // Single right rotation
}
// Right Heavy Case
if (balance < -1 && data > node.right.data) {
return leftRotate(node); // Single left rotation
}
// Left-Right Case
if (balance > 1 && data > node.left.data) {
return leftRightRotate(node); // Left-Right double rotation
}
// Right-Left Case
if (balance < -1 && data < node.right.data) {
return rightLeftRotate(node); // Right-Left double rotation
}
// Return the (unchanged) node pointer
return node;
}
// Delete a node from the AVL tree
public void delete(int data) {
root = deleteRec(root, data);
}
// Recursive function to delete a node
private Node deleteRec(Node root, int data) {
// 1. Perform the normal BST delete
if (root == null) {
return root;
}
if (data < root.data) {
root.left = deleteRec(root.left, data);
} else if (data > root.data) {
root.right = deleteRec(root.right, data);
} else {
// Node to be deleted found
// Case 1: Node has only one child or no child
if (root.left == null || root.right == null) {
Node temp = (root.left != null) ? root.left : root.right;
// No child case
if (temp == null) {
root = null;
} else {
root = temp; // Copy the contents of the non-empty child
}
} else {
// Case 2: Node has two children
Node temp = minValueNode(root.right);
// Copy the inorder successor's content to this node
root.data = temp.data;
// Delete the inorder successor
root.right = deleteRec(root.right, temp.data);
}
}
// If the tree only has one node, return it
if (root == null) {
return root;
}
// 2. Update the height of the current node
updateHeight(root);
// 3. Get the balance factor and perform rotations if necessary
int balance = balanceFactor(root);
// Left Heavy Case
if (balance > 1 && balanceFactor(root.left) >= 0) {
return rightRotate(root); // Single right rotation
}
// Right Heavy Case
if (balance < -1 && balanceFactor(root.right) <= 0) {
return leftRotate(root); // Single left rotation
}
// Left-Right Case
if (balance > 1 && balanceFactor(root.left) < 0) {
return leftRightRotate(root); // Left-Right double rotation
}
// Right-Left Case
if (balance < -1 && balanceFactor(root.right) > 0) {
return rightLeftRotate(root); // Right-Left double rotation
}
return root; // Return the (unchanged) node pointer
}
// Function to get the node with the minimum value (used for deletion)
private Node minValueNode(Node node) {
Node current = node;
while (current.left != null) {
current = current.left;
}
return current;
}
// In-order traversal (for testing purposes)
public void inorder() {
inorderRec(root);
}
private void inorderRec(Node root) {
if (root != null) {
inorderRec(root.left);
System.out.print(root.data + " ");
inorderRec(root.right);
}
}
// Pre-order traversal (for testing purposes)
public void preorder() {
preorderRec(root);
}
private void preorderRec(Node root) {
if (root != null) {
System.out.print(root.data + " ");
preorderRec(root.left);
preorderRec(root.right);
}
}
// Post-order traversal (for testing purposes)
public void postorder() {
postorderRec(root);
}
private void postorderRec(Node root) {
if (root != null) {
postorderRec(root.left);
postorderRec(root.right);
System.out.print(root.data + " ");
}
}
}
public class AVLTreeDemo {
public static void main(String[] args) {
AVLTree tree = new AVLTree();
// Insert nodes and ensure the tree remains balanced
tree.insert(10);
tree.insert(20);
tree.insert(30); // This will cause a rotation to keep the tree balanced
tree.insert(15);
// Display the tree in-order, pre-order, and post-order
System.out.print("In-order traversal: ");
tree.inorder(); // In-order should print the nodes in sorted order
System.out.println();
System.out.print("Pre-order traversal: ");
tree.preorder(); // Pre-order traversal
System.out.println();
System.out.print("Post-order traversal: ");
tree.postorder(); // Post-order traversal
System.out.println();
// Delete a node
tree.delete(20);
System.out.println("\nAfter deleting 20, the tree becomes balanced:");
// Display the tree again
System.out.print("In-order traversal: ");
tree.inorder(); // The tree should be balanced after deletion
System.out.println();
}
}

/////////////////////////////////////////////////////////////////////////////////////////////
999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999
Q9. Implement a graph using adjacency list representation. Perform the following:
i.
Traverse the graph using BFS.
ii.
Traverse the graph using DFS.
import java.util.*;
// Class to represent a Graph
class Graph {
// Map to store the adjacency list
private Map<Integer, List<Integer>> adjList;
// Constructor
public Graph() {
adjList = new HashMap<>();
}
// Add an edge to the graph (undirected graph)
public void addEdge(int u, int v) {
// Add edge u -> v
adjList.putIfAbsent(u, new ArrayList<>());
adjList.get(u).add(v);
// Add edge v -> u (since it's an undirected graph)
adjList.putIfAbsent(v, new ArrayList<>());
adjList.get(v).add(u);
}
// Perform BFS traversal of the graph starting from a given node
public void bfs(int start) {
// Create a visited set to track visited nodes
Set<Integer> visited = new HashSet<>();
// Create a queue for BFS
Queue<Integer> queue = new LinkedList<>();
// Start with the given node
visited.add(start);
queue.offer(start);
System.out.print("BFS traversal: ");
while (!queue.isEmpty()) {
int node = queue.poll();
System.out.print(node + " ");
// Visit all the neighbors of the current node
for (int neighbor : adjList.getOrDefault(node, new ArrayList<>())) {
if (!visited.contains(neighbor)) {
visited.add(neighbor);
queue.offer(neighbor);
}
}
}
System.out.println();
}
// Perform DFS traversal of the graph starting from a given node
public void dfs(int start) {
// Create a visited set to track visited nodes
Set<Integer> visited = new HashSet<>();
System.out.print("DFS traversal: ");
// Call the recursive DFS helper function
dfsHelper(start, visited);
System.out.println();
}
// Helper method for DFS using recursion
private void dfsHelper(int node, Set<Integer> visited) {
visited.add(node);
System.out.print(node + " ");
// Visit all the neighbors of the current node
for (int neighbor : adjList.getOrDefault(node, new ArrayList<>())) {
if (!visited.contains(neighbor)) {
dfsHelper(neighbor, visited);
}
}
}
// Utility method to print the graph (for testing)
public void printGraph() {
System.out.println("Graph adjacency list:");
for (int node : adjList.keySet()) {
System.out.print(node + ": ");
for (int neighbor : adjList.get(node)) {
System.out.print(neighbor + " ");
}
System.out.println();
}
}
}
public class GraphTraversal {
public static void main(String[] args) {
// Create a graph object
Graph graph = new Graph();
// Add edges to the graph
graph.addEdge(0, 1);
graph.addEdge(0, 2);
graph.addEdge(1, 3);
graph.addEdge(1, 4);
graph.addEdge(2, 5);
graph.addEdge(3, 6);
graph.addEdge(4, 6);
graph.addEdge(5, 6);
// Print the graph (adjacency list)
graph.printGraph();
// Perform BFS starting from node 0
graph.bfs(0);
// Perform DFS starting from node 0
graph.dfs(0);
}
}

//////////////////////////////////////////////////////////////////////////////////////////////////////////

Q10. Write a program to find the shortest path between two nodes in an unweighted graph using BFS.
import java.util.*;
// Class to represent a Graph
class Graph {
// Map to store the adjacency list
private Map<Integer, List<Integer>> adjList;
// Constructor
public Graph() {
adjList = new HashMap<>();
}
// Add an edge to the graph (undirected graph)
public void addEdge(int u, int v) {
adjList.putIfAbsent(u, new ArrayList<>());
adjList.get(u).add(v);
adjList.putIfAbsent(v, new ArrayList<>());
adjList.get(v).add(u);
}
// Perform BFS to find the shortest path from start to end
public List<Integer> findShortestPath(int start, int end) {
// Map to store the parent of each node in the BFS traversal
Map<Integer, Integer> parent = new HashMap<>();
// Set to store visited nodes
Set<Integer> visited = new HashSet<>();
// Queue for BFS
Queue<Integer> queue = new LinkedList<>();
// List to store the shortest path
List<Integer> path = new ArrayList<>();
// If start node is the same as end node, return the single node path
if (start == end) {
path.add(start);
return path;
}
// Start BFS from the 'start' node
visited.add(start);
queue.offer(start);
parent.put(start, null); // Start has no parent
while (!queue.isEmpty()) {
int current = queue.poll();
// Traverse all neighbors of the current node
for (int neighbor : adjList.getOrDefault(current, new ArrayList<>())) {
if (!visited.contains(neighbor)) {
visited.add(neighbor);
queue.offer(neighbor);
parent.put(neighbor, current);
// If we reached the end node, break and reconstruct the path
if (neighbor == end) {
reconstructPath(start, end, parent, path);
return path;
}
}
}
}
// If no path is found, return an empty list
return path;
}
// Reconstruct the path from the end node to the start node
private void reconstructPath(int start, int end, Map<Integer, Integer> parent, List<Integer> path) {
for (Integer node = end; node != null; node = parent.get(node)) {
path.add(node);
}
// Reverse the path to get it from start to end
Collections.reverse(path);
}
// Utility method to print the graph (for testing)
public void printGraph() {
System.out.println("Graph adjacency list:");
for (int node : adjList.keySet()) {
System.out.print(node + ": ");
for (int neighbor : adjList.get(node)) {
System.out.print(neighbor + " ");
}
System.out.println();
}
}
}
public class ShortestPathBFS {
public static void main(String[] args) {
// Create a graph object
Graph graph = new Graph();
// Add edges to the graph
graph.addEdge(0, 1);
graph.addEdge(0, 2);
graph.addEdge(1, 3);
graph.addEdge(1, 4);
graph.addEdge(2, 5);
graph.addEdge(3, 6);
graph.addEdge(4, 6);
graph.addEdge(5, 6);
// Print the graph (adjacency list)
graph.printGraph();
// Find the shortest path between nodes 0 and 6
List<Integer> shortestPath = graph.findShortestPath(0, 6);
// Print the shortest path
if (!shortestPath.isEmpty()) {
System.out.println("Shortest path from 0 to 6: " + shortestPath);
} else {
System.out.println("No path found between 0 and 6.");
}
}
}

////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
Q11. : Implement Topological Sort for a Directed Acyclic Graph (DAG) using Kahn’s Algorithm and DFS. Verify the result with a sample DAG.
import java.util.*;
// Class to represent a Directed Graph
class Graph {
private Map<Integer, List<Integer>> adjList;
// Constructor to initialize the graph
public Graph() {
adjList = new HashMap<>();
}
// Add an edge to the graph
public void addEdge(int u, int v) {
adjList.putIfAbsent(u, new ArrayList<>());
adjList.get(u).add(v);
}
// Kahn's Algorithm (BFS-based Topological Sort)
public List<Integer> topologicalSortKahn() {
Map<Integer, Integer> inDegree = new HashMap<>();
// Calculate in-degree of each node
for (int node : adjList.keySet()) {
inDegree.putIfAbsent(node, 0); // Make sure the node exists in the map
for (int neighbor : adjList.get(node)) {
inDegree.put(neighbor, inDegree.getOrDefault(neighbor, 0) + 1);
}
}
// Queue to store nodes with 0 in-degree
Queue<Integer> queue = new LinkedList<>();
for (int node : inDegree.keySet()) {
if (inDegree.get(node) == 0) {
queue.offer(node);
}
}
List<Integer> topologicalOrder = new ArrayList<>();
while (!queue.isEmpty()) {
int node = queue.poll();
topologicalOrder.add(node);
for (int neighbor : adjList.getOrDefault(node, new ArrayList<>())) {
inDegree.put(neighbor, inDegree.get(neighbor) - 1);
if (inDegree.get(neighbor) == 0) {
queue.offer(neighbor);
}
}
}
// If the topological order contains all nodes, return it; otherwise, there's a cycle
if (topologicalOrder.size() != adjList.size()) {
System.out.println("Graph contains a cycle, so topological sort is not possible.");
return new ArrayList<>();
}
return topologicalOrder;
}
// DFS-based Topological Sort
public List<Integer> topologicalSortDFS() {
Set<Integer> visited = new HashSet<>();
Stack<Integer> stack = new Stack<>();
Set<Integer> onStack = new HashSet<>(); // To detect cycles
List<Integer> result = new ArrayList<>();
// Perform DFS for all nodes
for (int node : adjList.keySet()) {
if (!visited.contains(node)) {
if (!topologicalSortDFSUtil(node, visited, stack, onStack, result)) {
System.out.println("Graph contains a cycle, so topological sort is not possible.");
return new ArrayList<>();
}
}
}
// Reverse the stack to get the topological order
while (!stack.isEmpty()) {
result.add(stack.pop());
}
return result;
}
// Helper method for DFS-based topological sort
private boolean topologicalSortDFSUtil(int node, Set<Integer> visited, Stack<Integer> stack, Set<Integer> onStack, List<Integer> result) {
visited.add(node);
onStack.add(node);
for (int neighbor : adjList.getOrDefault(node, new ArrayList<>())) {
if (onStack.contains(neighbor)) {
return false; // Cycle detected
}
if (!visited.contains(neighbor)) {
if (!topologicalSortDFSUtil(neighbor, visited, stack, onStack, result)) {
return false;
}
}
}
onStack.remove(node);
stack.push(node);
return true;
}
// Utility method to print the graph (for testing)
public void printGraph() {
System.out.println("Graph adjacency list:");
for (int node : adjList.keySet()) {
System.out.print(node + ": ");
for (int neighbor : adjList.get(node)) {
System.out.print(neighbor + " ");
}
System.out.println();
}
}
}
public class TopologicalSort {
public static void main(String[] args) {
// Create a graph object
Graph graph = new Graph();
// Add edges to the graph (Sample DAG)
graph.addEdge(5, 2);
graph.addEdge(5, 0);
graph.addEdge(4, 0);
graph.addEdge(4, 1);
graph.addEdge(2, 3);
graph.addEdge(3, 1);
// Print the graph (adjacency list)
graph.printGraph();
// Perform topological sort using Kahn's Algorithm (BFS)
List<Integer> topologicalOrderKahn = graph.topologicalSortKahn();
System.out.println("Topological Sort using Kahn's Algorithm (BFS): " + topologicalOrderKahn);
// Perform topological sort using DFS
List<Integer> topologicalOrderDFS = graph.topologicalSortDFS();
System.out.println("Topological Sort using DFS: " + topologicalOrderDFS);
}
}

//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
Q12. Write a program to implement Prim’s Algorithm to find the Minimum Spanning Tree (MST) of a connected, weighted graph. Represent the graph using an adjacency matrix.
import java.util.*;
public class PrimsAlgorithm {
// Function to implement Prim's Algorithm
public static void primMST(int[][] graph, int V) {
// Key values used to pick minimum weight edge in cut
int[] key = new int[V];
// To store parent array which is used to store MST
int[] parent = new int[V];
// To represent set of vertices included in MST
boolean[] inMST = new boolean[V];
// Initialize all keys as infinite
Arrays.fill(key, Integer.MAX_VALUE);
// Start with the first node (vertex 0)
key[0] = 0; // Make the first node's key value 0, so that it is picked first
parent[0] = -1; // No parent for the first node
// The MST will have V vertices
for (int count = 0; count < V - 1; count++) {
// Pick the minimum key vertex from the set of vertices not yet included in MST
int u = minKey(key, inMST, V);
// Include the picked vertex in MST
inMST[u] = true;
// Update the key and parent index of the adjacent vertices of the picked vertex
for (int v = 0; v < V; v++) {
// graph[u][v] is non-zero only for adjacent vertices of m
// Update the key only if graph[u][v] is smaller than key[v]
if (graph[u][v] != 0 && !inMST[v] && graph[u][v] < key[v]) {
key[v] = graph[u][v];
parent[v] = u;
}
}
}
// Print the constructed MST
printMST(parent, graph, V);
}
// Function to find the vertex with minimum key value
private static int minKey(int[] key, boolean[] inMST, int V) {
// Initialize min value
int min = Integer.MAX_VALUE, minIndex = -1;
// Search for the vertex with the minimum key value, from the set of vertices not yet included in MST
for (int v = 0; v < V; v++) {
if (!inMST[v] && key[v] < min) {
min = key[v];
minIndex = v;
}
}
return minIndex;
}
// Function to print the constructed MST
private static void printMST(int[] parent, int[][] graph, int V) {
System.out.println("Edge \tWeight");
for (int i = 1; i < V; i++) {
System.out.println(parent[i] + " - " + i + " \t" + graph[i][parent[i]]);
}
}
public static void main(String[] args) {
// Example adjacency matrix for a graph
int[][] graph = {
{0, 2, 0, 6, 0},
{2, 0, 3, 8, 5},
{0, 3, 0, 0, 7},
{6, 8, 0, 0, 9},
{0, 5, 7, 9, 0}
};
int V = graph.length; // Number of vertices in the graph
// Call Prim's algorithm to find MST
primMST(graph, V);
}
}

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
Q13. : Implement Kruskal’s Algorithm to find the Minimum Spanning Tree of a graph. Use the union-find technique to detect cycles.
import java.util.*;
// Edge class to represent an edge with weight
class Edge implements Comparable<Edge> {
int u, v, weight;
// Constructor
public Edge(int u, int v, int weight) {
this.u = u;
this.v = v;
this.weight = weight;
}
// Compare edges by weight
@Override
public int compareTo(Edge other) {
return Integer.compare(this.weight, other.weight);
}
}
// Union-Find (Disjoint Set) class
class UnionFind {
int[] parent, rank;
// Constructor
public UnionFind(int n) {
parent = new int[n];
rank = new int[n];
for (int i = 0; i < n; i++) {
parent[i] = i; // Initially, each node is its own parent
rank[i] = 0; // Initially, the rank of each node is 0
}
}
// Find the root of the set containing x, with path compression
public int find(int x) {
if (parent[x] != x) {
parent[x] = find(parent[x]); // Path compression
}
return parent[x];
}
// Union the sets containing x and y, with union by rank
public void union(int x, int y) {
int rootX = find(x);
int rootY = find(y);
if (rootX != rootY) {
// Union by rank
if (rank[rootX] > rank[rootY]) {
parent[rootY] = rootX;
} else if (rank[rootX] < rank[rootY]) {
parent[rootX] = rootY;
} else {
parent[rootY] = rootX;
rank[rootX]++;
}
}
}
}
// Kruskal's Algorithm to find the MST
public class KruskalMST {
// Function to implement Kruskal's Algorithm
public static void kruskalMST(int V, List<Edge> edges) {
// Sort edges by weight
Collections.sort(edges);
// Create Union-Find structure
UnionFind uf = new UnionFind(V);
// List to store the edges in the MST
List<Edge> mst = new ArrayList<>();
// Process edges
for (Edge edge : edges) {
int u = edge.u;
int v = edge.v;
// If u and v are in different sets, include this edge in MST
if (uf.find(u) != uf.find(v)) {
mst.add(edge);
uf.union(u, v); // Union the sets
}
// Stop when we have V-1 edges in the MST
if (mst.size() == V - 1) {
break;
}
}
// Print the MST
printMST(mst);
}
// Function to print the edges of the MST
private static void printMST(List<Edge> mst) {
System.out.println("Edges in MST:");
int mstWeight = 0;
for (Edge edge : mst) {
System.out.println(edge.u + " - " + edge.v + " : " + edge.weight);
mstWeight += edge.weight;
}
System.out.println("Total weight of MST: " + mstWeight);
}
public static void main(String[] args) {
// Example graph represented by edges (u, v, weight)
List<Edge> edges = new ArrayList<>();
edges.add(new Edge(0, 1, 10));
edges.add(new Edge(0, 2, 6));
edges.add(new Edge(0, 3, 5));
edges.add(new Edge(1, 3, 15));
edges.add(new Edge(2, 3, 4));
int V = 4; // Number of vertices in the graph
// Call Kruskal's algorithm to find the MST
kruskalMST(V, edges);
}
}

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
Q14. Write a program to find the shortest path between two vertices in a graph using Dijkstra's Algorithm. Test the program with both sparse and dense graphs.
import java.util.*;
// Class to represent an edge in the graph
class Edge {
int destination;
int weight;
// Constructor
public Edge(int destination, int weight) {
this.destination = destination;
this.weight = weight;
}
}
// Class to represent the graph using adjacency list
class Graph {
private List<List<Edge>> adjacencyList;
// Constructor
public Graph(int vertices) {
adjacencyList = new ArrayList<>();
for (int i = 0; i < vertices; i++) {
adjacencyList.add(new ArrayList<>());
}
}
// Add an edge to the graph
public void addEdge(int source, int destination, int weight) {
adjacencyList.get(source).add(new Edge(destination, weight));
adjacencyList.get(destination).add(new Edge(source, weight)); // For undirected graph
}
// Dijkstra's Algorithm to find the shortest path
public void dijkstra(int source, int destination) {
int V = adjacencyList.size();
int[] dist = new int[V]; // Distance from source to each vertex
Arrays.fill(dist, Integer.MAX_VALUE);
dist[source] = 0; // Distance to source is 0
// Min-heap (priority queue) to pick the vertex with the smallest distance
PriorityQueue<Integer> pq = new PriorityQueue<>(Comparator.comparingInt(v -> dist[v]));
pq.offer(source);
// Previous node array to reconstruct the path
int[] prev = new int[V];
Arrays.fill(prev, -1);
while (!pq.isEmpty()) {
int u = pq.poll(); // Vertex with the smallest distance
// If we reached the destination, stop
if (u == destination) {
break;
}
// Explore the neighbors of u
for (Edge edge : adjacencyList.get(u)) {
int v = edge.destination;
int weight = edge.weight;
// Relax the edge (u, v)
if (dist[u] + weight < dist[v]) {
dist[v] = dist[u] + weight;
prev[v] = u;
pq.offer(v); // Add the vertex to the priority queue
}
}
}
// Print the shortest path
printPath(prev, destination);
System.out.println("Shortest path distance: " + dist[destination]);
}
// Reconstruct and print the shortest path
private void printPath(int[] prev, int destination) {
if (prev[destination] == -1) {
System.out.println("No path found");
return;
}
// Reconstruct the path from destination to source
List<Integer> path = new ArrayList<>();
for (int at = destination; at != -1; at = prev[at]) {
path.add(at);
}
Collections.reverse(path); // Reverse to get the path from source to destination
System.out.print("Shortest path: ");
for (int vertex : path) {
System.out.print(vertex + " ");
}
System.out.println();
}
}
public class DijkstraAlgorithm {
public static void main(String[] args) {
// Test with Sparse Graph
System.out.println("Sparse Graph:");
Graph graph = new Graph(6);
graph.addEdge(0, 1, 1);
graph.addEdge(0, 2, 4);
graph.addEdge(1, 2, 2);
graph.addEdge(1, 3, 5);
graph.addEdge(2, 3, 1);
graph.addEdge(3, 4, 3);
graph.addEdge(4, 5, 6);
graph.dijkstra(0, 5); // Find the shortest path from vertex 0 to 5
// Test with Dense Graph
System.out.println("\nDense Graph:");
Graph denseGraph = new Graph(5);
denseGraph.addEdge(0, 1, 2);
denseGraph.addEdge(0, 2, 3);
denseGraph.addEdge(0, 3, 6);
denseGraph.addEdge(0, 4, 1);
denseGraph.addEdge(1, 2, 4);
denseGraph.addEdge(1, 3, 5);
denseGraph.addEdge(1, 4, 7);
denseGraph.addEdge(2, 3, 2);
denseGraph.addEdge(2, 4, 3);
denseGraph.addEdge(3, 4, 1);
denseGraph.dijkstra(0, 3); // Find the shortest path from vertex 0 to 3
}
}

//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
Q15. Write a program to implement Linear Search on a list of integers. Test the program by searching for an element present in the list and one not present in the list.
import java.util.*;
public class LinearSearch {
// Method to perform Linear Search on a list of integers
public static int linearSearch(List<Integer> list, int target) {
// Traverse through the list
for (int i = 0; i < list.size(); i++) {
// If the target is found, return the index
if (list.get(i) == target) {
return i;
}
}
// If target is not found, return -1
return -1;
}
public static void main(String[] args) {
// Create a list of integers
List<Integer> list = new ArrayList<>(Arrays.asList(12, 34, 7, 19, 3, 10, 5));
// Test 1: Searching for an element that is present in the list
int target1 = 19;
int result1 = linearSearch(list, target1);
if (result1 != -1) {
System.out.println("Element " + target1 + " found at index: " + result1);
} else {
System.out.println("Element " + target1 + " not found in the list.");
}
// Test 2: Searching for an element that is not present in the list
int target2 = 100;
int result2 = linearSearch(list, target2);
if (result2 != -1) {
System.out.println("Element " + target2 + " found at index: " + result2);
} else {
System.out.println("Element " + target2 + " not found in the list.");
}
}
}

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
Q16. : Write a program to implement Binary Search. Ensure that the list is sorted, and if not, sort it before performing the search.
import java.util.*;
public class BinarySearch {
// Method to perform Binary Search
public static int binarySearch(List<Integer> list, int target) {
// First, sort the list (if not already sorted)
Collections.sort(list);
int low = 0;
int high = list.size() - 1;
while (low <= high) {
int mid = low + (high - low) / 2;
// Check if the target is at the middle
if (list.get(mid) == target) {
return mid; // Target found at index 'mid'
}
// If the target is smaller, search the left half
else if (list.get(mid) > target) {
high = mid - 1;
}
// If the target is larger, search the right half
else {
low = mid + 1;
}
}
return -1; // Target not found
}
public static void main(String[] args) {
// Create a list of integers
List<Integer> list = new ArrayList<>(Arrays.asList(12, 3, 7, 19, 5, 1, 15));
// Test 1: Searching for an element that is present in the list
int target1 = 19;
int result1 = binarySearch(list, target1);
if (result1 != -1) {
System.out.println("Element " + target1 + " found at index: " + result1);
} else {
System.out.println("Element " + target1 + " not found in the list.");
}
// Test 2: Searching for an element that is not present in the list
int target2 = 100;
int result2 = binarySearch(list, target2);
if (result2 != -1) {
System.out.println("Element " + target2 + " found at index: " + result2);
} else {
System.out.println("Element " + target2 + " not found in the list.");
}
}
}

///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
Q17. Write a program to sort a list of integers using Merge Sort. Display the number of recursive calls made during the sorting process.
import java.util.*;
public class MergeSort {
// Variable to count the number of recursive calls
private static int recursiveCallCount = 0;
// Merge Sort method
public static void mergeSort(int[] arr, int left, int right) {
// Increment recursive call count
recursiveCallCount++;
// Base case: If the array has one element, return
if (left < right) {
int mid = (left + right) / 2;
// Recursively sort the left half
mergeSort(arr, left, mid);
// Recursively sort the right half
mergeSort(arr, mid + 1, right);
// Merge the two halves
merge(arr, left, mid, right);
}
}
// Merge method to merge two sorted halves
public static void merge(int[] arr, int left, int mid, int right) {
// Create temporary arrays for the two halves
int n1 = mid - left + 1;
int n2 = right - mid;
int[] leftArr = new int[n1];
int[] rightArr = new int[n2];
// Copy data to temporary arrays
System.arraycopy(arr, left, leftArr, 0, n1);
System.arraycopy(arr, mid + 1, rightArr, 0, n2);
// Merge the temporary arrays back into the original array
int i = 0, j = 0, k = left;
while (i < n1 && j < n2) {
if (leftArr[i] <= rightArr[j]) {
arr[k] = leftArr[i];
i++;
} else {
arr[k] = rightArr[j];
j++;
}
k++;
}
// Copy the remaining elements of leftArr[] if any
while (i < n1) {
arr[k] = leftArr[i];
i++;
k++;
}
// Copy the remaining elements of rightArr[] if any
while (j < n2) {
arr[k] = rightArr[j];
j++;
k++;
}
}
// Method to print the array
public static void printArray(int[] arr) {
for (int num : arr) {
System.out.print(num + " ");
}
System.out.println();
}
public static void main(String[] args) {
// Sample input array
int[] arr = {12, 3, 7, 19, 5, 1, 15};
// Print original array
System.out.print("Original Array: ");
printArray(arr);
// Perform merge sort
mergeSort(arr, 0, arr.length - 1);
// Print sorted array
System.out.print("Sorted Array: ");
printArray(arr);
// Print the number of recursive calls
System.out.println("Number of recursive calls: " + recursiveCallCount);
}
}

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
Q18. : Implement Quick Sort to sort an array of integers. Allow the user to input a pivot selection strategy (first element, last element, or median).
import java.util.*;
public class QuickSort {
// Method to perform Quick Sort
public static void quickSort(int[] arr, int low, int high, String pivotStrategy) {
if (low < high) {
// Get the pivot index after partitioning
int pivotIndex = partition(arr, low, high, pivotStrategy);
// Recursively sort the left and right sub-arrays
quickSort(arr, low, pivotIndex - 1, pivotStrategy);
quickSort(arr, pivotIndex + 1, high, pivotStrategy);
}
}
// Partition method that arranges elements around the pivot
public static int partition(int[] arr, int low, int high, String pivotStrategy) {
int pivot = choosePivot(arr, low, high, pivotStrategy);
// Swap the pivot to the end of the array
swap(arr, pivot, high);
int i = low - 1;
for (int j = low; j < high; j++) {
if (arr[j] <= arr[high]) {
i++;
swap(arr, i, j);
}
}
// Swap the pivot element back to its correct position
swap(arr, i + 1, high);
return i + 1; // Return the index of the pivot
}
// Method to choose the pivot based on the selected strategy
public static int choosePivot(int[] arr, int low, int high, String pivotStrategy) {
int pivotIndex = low;
switch (pivotStrategy.toLowerCase()) {
case "first":
pivotIndex = low;
break;
case "last":
pivotIndex = high;
break;
case "median":
pivotIndex = medianOfThree(arr, low, high);
break;
default:
System.out.println("Invalid pivot strategy. Defaulting to first element.");
pivotIndex = low;
break;
}
return pivotIndex;
}
// Helper method to choose the median of the first, middle, and last elements
public static int medianOfThree(int[] arr, int low, int high) {
int mid = low + (high - low) / 2;
int[] candidates = {arr[low], arr[mid], arr[high]};
Arrays.sort(candidates);
if (candidates[1] == arr[low]) return low;
if (candidates[1] == arr[mid]) return mid;
return high;
}
// Helper method to swap elements in the array
public static void swap(int[] arr, int i, int j) {
int temp = arr[i];
arr[i] = arr[j];
arr[j] = temp;
}
// Method to print the array
public static void printArray(int[] arr) {
for (int num : arr) {
System.out.print(num + " ");
}
System.out.println();
}
public static void main(String[] args) {
Scanner sc = new Scanner(System.in);
// Input array from user
System.out.print("Enter the number of elements: ");
int n = sc.nextInt();
int[] arr = new int[n];
System.out.print("Enter the elements: ");
for (int i = 0; i < n; i++) {
arr[i] = sc.nextInt();
}
// Ask user for the pivot strategy
System.out.println("Choose pivot strategy: ");
System.out.println("1. First element");
System.out.println("2. Last element");
System.out.println("3. Median of first, middle, and last element");
System.out.print("Enter your choice (first/last/median): ");
String pivotStrategy = sc.next();
// Print original array
System.out.print("Original Array: ");
printArray(arr);
// Perform quick sort
quickSort(arr, 0, arr.length - 1, pivotStrategy);
// Print sorted array
System.out.print("Sorted Array: ");
printArray(arr);
sc.close();
}
}

///////////////////////////////////////////////////////////////////////////////////
Q19. Write a program to implement a heap data structure. Perform the following operations:
1.
Insert an element into a min-heap.
2.
Delete the minimum element.
3.
Convert the heap to a max-heap
import java.util.*;
public class Heap {
private List<Integer> heap; // List to store heap elements
public Heap() {
this.heap = new ArrayList<>();
}
// Method to insert an element into the min-heap
public void insert(int value) {
heap.add(value); // Add element at the end
heapifyUp(heap.size() - 1); // Restore heap property
}
// Method to delete the minimum element (root) from the min-heap
public int deleteMin() {
if (heap.size() == 0) {
throw new NoSuchElementException("Heap is empty.");
}
int min = heap.get(0); // The minimum element is at the root
int lastElement = heap.remove(heap.size() - 1); // Remove the last element
if (heap.size() > 0) {
heap.set(0, lastElement); // Replace root with the last element
heapifyDown(0); // Restore heap property
}
return min;
}
// Method to restore the heap property by "bubbling up"
private void heapifyUp(int index) {
while (index > 0) {
int parentIndex = (index - 1) / 2;
if (heap.get(index) >= heap.get(parentIndex)) {
break; // No violation of heap property
}
// Swap current element with its parent
swap(index, parentIndex);
index = parentIndex;
}
}
// Method to restore the heap property by "bubbling down"
private void heapifyDown(int index) {
int leftChildIndex = 2 * index + 1;
int rightChildIndex = 2 * index + 2;
int smallest = index;
if (leftChildIndex < heap.size() && heap.get(leftChildIndex) < heap.get(smallest)) {
smallest = leftChildIndex;
}
if (rightChildIndex < heap.size() && heap.get(rightChildIndex) < heap.get(smallest)) {
smallest = rightChildIndex;
}
if (smallest != index) {
swap(index, smallest);
heapifyDown(smallest);
}
}
// Method to swap two elements in the heap
private void swap(int i, int j) {
int temp = heap.get(i);
heap.set(i, heap.get(j));
heap.set(j, temp);
}
// Method to convert the min-heap to a max-heap
public void convertToMaxHeap() {
for (int i = (heap.size() / 2) - 1; i >= 0; i--) {
maxHeapify(i);
}
}
// Method to restore the max-heap property
private void maxHeapify(int index) {
int leftChildIndex = 2 * index + 1;
int rightChildIndex = 2 * index + 2;
int largest = index;
if (leftChildIndex < heap.size() && heap.get(leftChildIndex) > heap.get(largest)) {
largest = leftChildIndex;
}
if (rightChildIndex < heap.size() && heap.get(rightChildIndex) > heap.get(largest)) {
largest = rightChildIndex;
}
if (largest != index) {
swap(index, largest);
maxHeapify(largest);
}
}
// Method to print the heap
public void printHeap() {
System.out.println(heap);
}
public static void main(String[] args) {
Heap minHeap = new Heap();
// Insert elements into the min-heap
minHeap.insert(10);
minHeap.insert(5);
minHeap.insert(3);
minHeap.insert(8);
minHeap.insert(2);
minHeap.insert(7);
minHeap.insert(1);
// Print the min-heap
System.out.print("Min-Heap: ");
minHeap.printHeap();
// Delete the minimum element (root)
System.out.println("Deleted Minimum: " + minHeap.deleteMin());
System.out.print("Min-Heap after deletion: ");
minHeap.printHeap();
// Convert the min-heap to a max-heap
minHeap.convertToMaxHeap();
System.out.print("Max-Heap: ");
minHeap.printHeap();
}
}

////////////////////////////////////////////////////////////////
Q20. : Implement a hash table with the following operations:
1.
Insert an element.
2.
Search for an element.
3.
Handle collisions using chaining or open addressing.
import java.util.LinkedList;
public class HashTable {
// Hash Table size
private static final int SIZE = 10;
// Array to store chains (linked lists) for collision handling
private LinkedList<Node>[] table;
// Constructor to initialize the hash table
public HashTable() {
table = new LinkedList[SIZE];
for (int i = 0; i < SIZE; i++) {
table[i] = new LinkedList<>();
}
}
// Node class to store key-value pairs
private static class Node {
String key;
String value;
Node(String key, String value) {
this.key = key;
this.value = value;
}
}
// Hash function to map keys to indices in the table
private int hash(String key) {
return key.hashCode() % SIZE;
}
// Insert a key-value pair into the hash table
public void insert(String key, String value) {
int index = hash(key);
LinkedList<Node> chain = table[index];
// Check if the key already exists in the chain
for (Node node : chain) {
if (node.key.equals(key)) {
node.value = value; // Update the value if the key already exists
return;
}
}
// If the key does not exist, add a new node to the chain
chain.add(new Node(key, value));
}
// Search for a value by key
public String search(String key) {
int index = hash(key);
LinkedList<Node> chain = table[index];
// Search for the key in the chain
for (Node node : chain) {
if (node.key.equals(key)) {
return node.value; // Return the value if the key is found
}
}
// Return null if the key is not found
return null;
}
// Print the hash table for debugging purposes
public void printTable() {
for (int i = 0; i < SIZE; i++) {
System.out.print("Index " + i + ": ");
for (Node node : table[i]) {
System.out.print("[" + node.key + " -> " + node.value + "] ");
}
System.out.println();
}
}
public static void main(String[] args) {
// Create a new hash table
HashTable hashTable = new HashTable();
// Insert some key-value pairs into the hash table
hashTable.insert("apple", "fruit");
hashTable.insert("carrot", "vegetable");
hashTable.insert("banana", "fruit");
hashTable.insert("tomato", "vegetable");
hashTable.insert("melon", "fruit");
// Search for some elements
System.out.println("apple: " + hashTable.search("apple")); // Should print "fruit"
System.out.println("banana: " + hashTable.search("banana")); // Should print "fruit"
System.out.println("carrot: " + hashTable.search("carrot")); // Should print "vegetable"
System.out.println("tomato: " + hashTable.search("tomato")); // Should print "vegetable"
System.out.println("melon: " + hashTable.search("melon")); // Should print "fruit"
System.out.println("grape: " + hashTable.search("grape")); // Should print "null"
// Print the hash table to see the chains
hashTable.printTable();
}
}
