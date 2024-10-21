05/16/2023 | U500 |Generate | Continuation | Recursion | Brian Eddow 


## Prompt: Comment on the use of recursion in JavaScript 

Recursion can be a mind-bending topic to approach. This method works by 

 
### Completion:  

calling the function from within itself. This may not make much sense to the reader who isn’t familiar with the stack data type. Since recursion relies on the stack and its behavior, let’s talk about what this means. 

A stack data type is analogous to a stack of dinner plates. Each one sits atop the other. You can only pull one plate off the stack or place one plate on the stack at once. This represents a last-in-first-out flow of plates (data). Now, keep in mind the return value from each plate. With recursion, each plate represents a function, the same function that’s called from within itself. Each function in the stack remembers all the data declared in it. Likewise, recursion requires a base case return statement (the initial if check below). Once the inputs to the function equal a certain value, the base case tells the function to start removing plates from the stack. These plates return a value that is sent to the plate, or function, beneath it. 

```
function MyFunc(n) { 

  if (n === 1) return n; 

  return n + MyFunc(n-1); 

}
```

This bit of code uses recursion to sum any number `N + n-1 + n-2 … n-(n-1)`. If you pass 10 into the function call, you’ll get `10 + 9 + 8 + 7 + 6 + 5 + 4 + 3 + 2 + 1`. Why does it stop at one? The first line of the function asks: `is the value of N equal to one? If it is, return N`. Without this base case, a recursively written function will never return anything (aka stack overflow). 

 
```
MyFunc(10-9) // Triggers the if-check for a base case. Since 10 minus 9 equals one (our base case), the stack begins to return functions and their values. 

MyFunc(10-8) // returns 2 once the base case is met.

…  

MyFunc(10-2) // returns 8 once the base case is met.

MyFunc(10-1) // returns 9 once the base case is met.

MyFunc(10) // initial function call 
```
 

Curiously, the base case is triggered at the top of the stack, then returns a number from each function (plate) descending the stack. The original function call will receive an accumulated number depending on the final line of code in the recursive function.  

`return n + MyFunc(n-1)`

The part after the return keyword declares how the stack should handle values returned from hitting the base case at the top of the stack. This recursive call asks the stack to sum return values. 

`return n * MyFunc(n/2)`

This recursive call tells the stack to multiply return values after hitting the base case. It also dictates that recursive calls will be supplied with half the n value of the previous call. 

`MyFunc(60) → MyFunc(30) → MyFunc(15)`


Happy coding! 


> [!NOTE]
> This content was produced to seed Amazon's bedrock generative AI service, Titan.
