
Implement Queue using Stacks
Easy
Company Tags
Implement a first in first out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a normal queue (push, peek, pop, and empty).

Implement the MyQueue class:

void push(int x) Pushes element x to the back of the queue.
int pop() Removes the element from the front of the queue and returns it.
int peek() Returns the element at the front of the queue.
boolean empty() Returns true if the queue is empty, false otherwise.
Notes:

You must use only standard operations of a stack, which means only push to top, peek/pop from top, size, and is empty operations are valid.
Depending on your language, the stack may not be supported natively. You may simulate a stack using a list or deque (double-ended queue) as long as you use only a stack's standard operations.
Example 1:

Input: ["MyQueue", "push", "push", "peek", "pop", "empty"]
[[], [1], [2], [], [], []]

Output: [null, null, null, 1, 1, false]
Explanation:
MyQueue myQueue = new MyQueue();
myQueue.push(1); // queue is: [1]
myQueue.push(2); // queue is: [1, 2] (leftmost is front of the queue)
myQueue.peek(); // return 1
myQueue.pop(); // return 1, queue is [2]
myQueue.empty(); // return false

Constraints:

1 <= x <= 9
At most 100 calls will be made to push, pop, peek, and empty.
All the calls to pop and peek are valid.
Follow-up: Can you implement the queue such that each operation is amortized O(1) time complexity? In other words, performing n operations will take overall O(n) time even if one of those operations may take longer.


-------------------------------------------------------------------
<img width="1277" height="713" alt="image" src="https://github.com/user-attachments/assets/19ed68e1-3b84-472b-ac64-b5a3bfb2ecdb" />

-------------------------------------------------------------------

    package leetcode.easy;
    
    import java.util.Stack;
    
    public class MyQueue {
    
      private final Stack<Integer> input;
      private final Stack<Integer> output;
    
      public MyQueue() {
        input = new Stack<>();
        output = new Stack<>();
      }
    
      public void push(int x) {
        input.push(x);
      }
      public int pop() {
        peek();
        return output.pop();
      }
      public int peek() {
        if (output.empty())
          while (!input.empty())
            output.push(input.pop());
        return output.peek();
      }
      public boolean empty() {
        return input.empty() && output.empty();
      }
    
      public static void main(String[] args) {
        MyQueue queue = new MyQueue();
        queue.push(1);
        queue.push(2);
        System.out.println(queue.peek());  // returns 1
        System.out.println(queue.pop());   // returns 1
        System.out.println(queue.empty()); // returns false
      }
    
    }
-------------------------------------------------------------------------------------------------------

time - O(n)
space - O(n)

------------------------------------------------------------------------------------

    class MyQueue {
        Stack<Integer> q;
        Stack<Integer> w;
        public MyQueue() {
            q = new Stack<>();
            w = new Stack<>();
        }
        
        public void push(int x) {
            q.push(x);
        }
        
        public int pop() {
            if(w.isEmpty()){
                while(!q.isEmpty()){
                    w.push(q.pop());
                }
            }
            return w.pop();
        }
        
        public int peek() {
            if(w.isEmpty()){
                while(!q.isEmpty()){
                    w.push(q.pop());
                }
            }
            return w.peek();
        }
        
        public boolean empty() {
            return q.isEmpty() && w.isEmpty();
        }
    }
    
    /**
     * Your MyQueue object will be instantiated and called as such:
     * MyQueue obj = new MyQueue();
     * obj.push(x);
     * int param_2 = obj.pop();
     * int param_3 = obj.peek();
     * boolean param_4 = obj.empty();
     */
