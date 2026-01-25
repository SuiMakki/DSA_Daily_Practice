Asteroid Collision
Solved 
Medium
Company Tags
You are given an array asteroids of integers representing asteroids in a row. The indices of the asteriod in the array represent their relative position in space.

For each asteroid, the absolute value represents its size, and the sign represents its direction (positive meaning right, negative meaning left). Each asteroid moves at the same speed.

Find out the state of the asteroids after all collisions. If two asteroids meet, the smaller one will explode. If both are the same size, both will explode. Two asteroids moving in the same direction will never meet.

Example 1:

Input: asteroids = [2,4,-4,-1]

Output: [2]
Example 2:

Input: asteroids = [5,5]

Output: [5,5]
Example 3:

Input: asteroids = [7,-3,9]

Output: [7,9]
Constraints:

2 <= asteroids.length <= 10,000.
-1000 <= asteroids[i] <= 1000
asteroids[i] != 0

---------------------------------------------------------------------------------------
      class Solution {
            public int[] asteroidCollision(int[] asteroids) {
               Stack<Integer> stack = new Stack<>();
        
                for (int ast : asteroids) {
                    boolean exploded = false;
        
                    // Collision condition: Top is moving right (+) and current is moving left (-)
                    while (!stack.isEmpty() && ast < 0 && stack.peek() > 0) {
                        if (stack.peek() < -ast) {
                            stack.pop(); // Top asteroid is smaller, it explodes
                            continue;    // Continue to check next asteroid in stack
                        } else if (stack.peek() == -ast) {
                            stack.pop(); // Both are same size, both explode
                            exploded = true;
                            break;
                        } else {
                            exploded = true; // Current asteroid is smaller, it explodes
                            break;
                        }
                    }
        
                    if (!exploded) {
                        stack.push(ast);
                    }
                }
        
                // Convert Stack to int array for the result
                int[] result = new int[stack.size()];
                for (int i = result.length - 1; i >= 0; i--) {
                    result[i] = stack.pop();
                }
                return result;
            }
        }

-------------------------------------------------------------------------------------------------O(n)---O(n)

This problem is a classic application of the Stack data structure. The stack helps us keep track of asteroids moving to the right (positive) and resolve collisions whenever we encounter an asteroid moving to the left (negative).

The Logic (Flash Card Style)
Positive Asteroid (> 0): No collision possible yet. Just Push it onto the stack.

Negative Asteroid (< 0): It might collide with the ones already in the stack.

Condition for Collision: A collision only happens if the top of the stack is positive (moving right) and the current asteroid is negative (moving left).

Resolution:

If |stack.top| < |current|: The top asteroid explodes. Pop and continue checking the next top.

If |stack.top| == |current|: Both explode. Pop and stop.

If |stack.top| > |current|: The current asteroid explodes. Stop (do not push current).

Pattern: Monotonic-like StackThis problem uses a stack to process elements in a linear fashion while resolving interactions based on direction. 
It’s similar to the Valid Parentheses problem you worked on earlier, where the "opening" bracket is the right-moving asteroid and the "closing" bracket is the left-moving asteroid.
Resume ConnectionFor your NxtWave application, mention that you are proficient in Data Structures and Algorithms, specifically using Stacks to solve complex linear simulations with $O(n)$ efficiency.
