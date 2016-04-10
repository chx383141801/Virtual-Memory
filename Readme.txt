Implementation Details:
pthread library has been implemented with create, yield, exit and join functions. Also, mutex init, lock unlock and destroy functions have been implemented.
We have implemented a scheduler with a queue of time quantum 50ms and execute with Round Robin. The scheduler works by initially giving any new process the highest priority and if it doesn’t finish execution within the given 50ms then it gets lower priority and goes to next queue with a time quantum of 100ms. Since we are using a round robin technique, all processes will definitely run to completion within the restrictions of priority it is given. For switching to another queue we are using a signal handler that will initiate a context switch using ucontext library which provides us with makecontext, setcontext, and swapcontext functions. We have written our scheduler in such a manner that 3 threads will run for 50ms and then it will run for 100ms thereafter it runs for 50ms again by bumping up its priority. This way we are ensuring that CPU utilization is maximized using a maintenance cycle.
Testing results:
We had 3 threads running as test. They were mythread, Fibonacci and squares.
myThread – Prints the numbers from 0 to 5
Fibonacci – Prints Fibonacci numbers upto 15th iteration
Squares – Prints the squares of numbers from 0 to 9
