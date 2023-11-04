### Question: 735. Asteroid Collision

**Medium**

We are given an array asteroids of integers representing asteroids in a row.

For each asteroid, the absolute value represents its size, and the sign represents its direction (positive meaning right, negative meaning left). Each asteroid moves at the same speed.

Find out the state of the asteroids after all collisions. If two asteroids meet, the smaller one will explode. If both are the same size, both will explode. Two asteroids moving in the same direction will never meet.

 

Example 1:

Input: asteroids = [5,10,-5]
Output: [5,10]
Explanation: The 10 and -5 collide resulting in 10. The 5 and 10 never collide.

Example 2:

Input: asteroids = [8,-8]
Output: []
Explanation: The 8 and -8 collide exploding each other.

Example 3:

Input: asteroids = [10,2,-5]
Output: [10]
Explanation: The 2 and -5 collide resulting in -5. The 10 and -5 collide resulting in 10.
 

Constraints:

2 <= asteroids.length <= 104

-1000 <= asteroids[i] <= 1000

asteroids[i] != 0


### Answer:
Python implementation using Object-Oriented Programming (OOP) principles to solve the "Asteroid Collision" problem:
```python
class AsteroidCollision:
    @staticmethod
    def asteroidCollision(asteroids):
        stack = []
        for asteroid in asteroids:
            while stack and asteroid < 0 < stack[-1]:
                if stack[-1] < -asteroid:
                    stack.pop()
                    continue
                elif stack[-1] == -asteroid:
                    stack.pop()
                break
            else:
                stack.append(asteroid)
        return stack

# Test cases
asteroids1 = [5, 10, -5]
print(AsteroidCollision.asteroidCollision(asteroids1))  # Output: [5, 10]

asteroids2 = [8, -8]
print(AsteroidCollision.asteroidCollision(asteroids2))  # Output: []

asteroids3 = [10, 2, -5]
print(AsteroidCollision.asteroidCollision(asteroids3))  # Output: [10]

```
This code defines a class AsteroidCollision with a static method asteroidCollision that implements the logic for finding the state of the asteroids after all collisions. The method uses a stack to simulate the collisions between asteroids, and the final state of the asteroids is returned based on the collision rules provided in the problem description.

### Explanation 

```python
class AsteroidCollision:
    @staticmethod
    def asteroidCollision(asteroids):
        stack = []  # We create an empty space to store our rocks.

        for asteroid in asteroids:  # We look at each rock in our line of rocks.
            while stack and asteroid < 0 < stack[-1]:  # If a rock is moving left and the one in the stack is moving right:
                if stack[-1] < -asteroid:  # If the rock in the stack is smaller than the current left-moving rock:
                    stack.pop()  # The smaller rock gets destroyed and disappears.
                    continue  # We go back to looking at the next rock in the stack.
                elif stack[-1] == -asteroid:  # If they are the same size:
                    stack.pop()  # Both rocks get destroyed.
                break  # We stop looking at these two rocks.

            else:  # If the rocks are not meeting each other:
                stack.append(asteroid)  # We add the rock to the line-up.

        return stack  # At the end, we show the rocks that are left after all the crashing.

```

This code creates a process to manage and decide what happens when rocks, which are moving in different directions, meet each other in a line. It goes through each rock and decides their fate based on the rules given in the explanation, finally showing us which rocks are left after they meet and crash.




