# Assignment Questions

## Instructions
Answer all 4 questions with detailed explanations. Each answer should be **3-5 sentences minimum** and demonstrate your understanding of the concepts.

---

## Question 1: Thread vs Process

**Question**: Explain the difference between a **thread** and a **process**. Why did we use threads in this assignment instead of creating separate processes?

**Your Answer:**
A process is an independent program in execution that has its own memory space, system resources, and state. In contrast, a thread is a smaller unit of execution within a process and shares the same memory and resources with other threads in that process. Processes are more expensive to create and manage because they require separate memory allocation and higher system overhead. Threads, however, are lightweight and faster to create, making them more efficient for concurrent execution. In this assignment, threads were used instead of processes because they allow efficient simulation of multiple processes within a single program. This makes it easier to implement scheduling algorithms like Round Robin while reducing complexity and resource usage
[Write your answer here. Consider: What is a process? What is a thread? How do they differ in terms of memory, resources, creation overhead? Why are threads more suitable for this simulation?]

---

## Question 2: Ready Queue Behavior

**Question**: In Round-Robin scheduling, what happens when a process doesn't finish within its time quantum? Explain using an example from your program output.

**Your Answer:**
In Round Robin scheduling, when a process does not finish execution within its assigned time quantum, it is moved to the end of the ready queue. This allows other processes to get their turn on the CPU, ensuring fairness among all processes. The process will wait until its turn comes again and then continue execution from where it stopped
[Write your answer here. Describe the specific behavior - where does the process go? When does it run again? Give an example from your actual program output showing a process that was re-queued.]

Example from my output:
```
P1 completed quantum 4000ms │ Overall progress: 74%
Remaining time: 1387ms
P1 yields CPU for context switch
P1 added to ready queue
```

**Explanation of example:**
[Explain what's happening in the output snippet you pasted]
In this example, process P1 was given a time quantum of 4000ms but did not complete execution because it still had 1387ms remaining. As a result, it yielded the CPU and was placed back at the end of the ready queue. Later in the simulation, P1 gets another turn and continues execution until it finishes. This behavior ensures fairness and prevents any single process from monopolizing the CPU
---

## Question 3: Thread States

**Question**: A thread can be in different states: **New**, **Runnable**, **Running**, **Waiting**, **Terminated**. Walk through these states for one process (P1) from your simulation.

**Your Answer:**

[Write your answer here. For each state, explain when P1 enters that state during the simulation. Use your understanding of the code to trace through the lifecycle.]

1. **New**: [When is P1 in New state?]P1 is in the New state when the thread object is created using `new Thread(process)` but before calling the `start()` method.

2. **Runnable**: [When does P1 become Runnable?]After calling `start()`, P1 enters the Runnable state and becomes ready to be scheduled by the CPU.

3. **Running**: [When is P1 Running?]P1 is in the Running state when its `run()` method is actively executing during its assigned time quantum

4. **Waiting**: [When/why would P1 be Waiting?]P1 enters the Waiting state when `Thread.sleep()` is called inside the `run()` method to simulate execution delay, or when `join()` is used by the main thread to wait for its completion.

5. **Terminated**: [When is P1 Terminated?]P1 reaches the Terminated state when it finishes execution completely and its remaining time becomes zero

---

## Question 4: Real-World Applications

**Question**: Give **TWO** real-world examples where Round-Robin scheduling with threads would be useful. Explain why this scheduling algorithm works well for those scenarios.

**Your Answer:**

### Example 1: [Web Browser Tabs]

**Description**: 
[Modern web browsers allow users to open multiple tabs, where each tab runs independently and loads different web pages]

**Why Round-Robin works well here**: 
[Round Robin scheduling ensures that each tab gets a fair share of CPU time. This prevents one tab from freezing the entire browser and improves responsiveness for the user.]

### Example 2: [Operating System Task Scheduling]

**Description**: 
[Operating systems handle multiple running applications and background processes at the same time.]

**Why Round-Robin works well here**: 
[Round Robin scheduling ensures fairness by giving each process a fixed time slice. This prevents starvation and ensures that all processes receive CPU time, improving system responsiveness and stability.]

---

## Summary

**Key concepts I understood through these questions:**
1. The difference between threads and processes
2. How Round Robin scheduling manages the ready queue
3. Thread lifecycle and state transitions

**Concepts I need to study more:**
1. Deadlocks and race conditions  
2. Thread synchronization and locks  
