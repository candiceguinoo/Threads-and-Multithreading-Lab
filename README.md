# Threads and Multithreading Laboratory

## Student Information
- Name: Candice Guinoo
- Section: B186
- Date: November 17, 2026

## Laboratory Description
This laboratory demonstrates thread creation, multithreading, thread coordination, and shared-resource management using Python.

## Completed Tasks

### Task 1 – Single Thread

**Description:**

Created and executed a single thread using `threading.Thread()`. The thread displays numbers from 1 to 5 with a one-second delay between each number.

**Expected Result:**
```text
Number: 1
Number: 2
Number: 3
Number: 4
Number: 5
Program completed.
```

**Actual Result:**

The program successfully displayed numbers 1 to 5, followed by "Program completed." The output matched the expected result.

**Screenshot:**

<img width="687" height="123" alt="image" src="https://github.com/user-attachments/assets/19ef3141-cb18-44f3-9182-7930f8dab9db" />



**Guide Questions and Answers:**

1. **What is the purpose of `threading.Thread()`?**

   It creates a new thread that can execute a function separately from the main program.

2. **What happens when `start()` is executed?**

   It starts the thread and allows the assigned function to run.

3. **What is the purpose of `join()`?**

   It makes the main program wait until the thread finishes its execution.

4. **What happens if `join()` is removed?**

   The main program does not wait for the thread and may continue while the thread is still running.

### Task 2 – Multiple Threads
---

**Description:**

Created two threads that execute different functions. Both threads display numbers from 1 to 5, demonstrating concurrent execution.

**Expected Result:**

The two threads display their numbers, and the output order may vary.

```text
Thread 1: 1
Thread 2: 1
Thread 1: 2
Thread 2: 2
Thread 1: 3
Thread 2: 3
Thread 1: 4
Thread 2: 4
Thread 1: 5
Thread 2: 5
Both threads completed.
```

**Actual Result:**

Both threads successfully displayed numbers from 1 to 5. The order of the output was different from the sample, but both threads completed successfully.

```text
Thread 1: 1
Thread 2: 1
Thread 2: 2
Thread 1: 2
Thread 1: 3
Thread 2: 3
Thread 1: 4
Thread 2: 4
Thread 1: 5
Thread 2: 5
Both threads completed.
```

**Screenshot:**

<img width="698" height="213" alt="image" src="https://github.com/user-attachments/assets/c743b8f4-b187-4634-890a-4ee5e833c02a" />

**Guide Questions and Answers:**

1. **How many threads are created in the program?**

   Two threads are created: Thread 1 and Thread 2.

2. **Do the two threads execute independently?**

   Yes. Each thread runs its own function, allowing them to execute concurrently.

3. **Why might the output order change when the program is executed again?**

   The operating system scheduler decides when each thread executes, so the output order may change.

4. **What is the difference between sequential and concurrent execution?**

   Sequential execution means tasks run one after another. Concurrent execution means multiple tasks make progress during the same period.

### Task 3 – Thread Synchronization Using `join()`
---

**Description:**

Created a thread that simulates downloading a file. Used `join()` to make the main program wait until the download thread finishes.

**Expected Result (with `join()`):**
```text
Downloading file...
Main program is waiting...
Download completed.
Main program continues.
```

**Actual Result (with `join()`):**

The main program waited until the download was completed before continuing. The output matched the expected result.

**Screenshot:**

<img width="731" height="90" alt="image" src="https://github.com/user-attachments/assets/299c366f-c3cf-4018-8fc0-04590f9b699f" />

**Actual Result (without `join()`):**

After removing `t1.join()`, the main program continued before the download thread finished.

```text
Downloading file...
Main program is waiting...
Main program continues.
Download completed.
```

**Screenshot:**

<img width="738" height="88" alt="image" src="https://github.com/user-attachments/assets/c2e62977-8c69-463e-b3d1-46ef601ef82f" />

**Guide Questions and Answers:**

1. **Why does the main program wait when `join()` is used?**

   Because `join()` makes the main program wait until the thread finishes.

2. **What happens when `join()` is removed?**

   The main program can continue without waiting for the thread to finish.

3. **In what situations is thread synchronization necessary?**

   It is necessary when threads need to coordinate their tasks or access shared data to avoid conflicts.

### Task 4 – Managing Shared Resources Using Thread Locks
---

**Description:**

Created two threads that increment the same counter. Used `threading.Lock()` to prevent both threads from modifying the shared counter at the same time.

**Expected Result (with lock):**
```text
Final Counter: 200000
```

**Actual Result (with lock):**

The program successfully displayed `Final Counter: 200000`, which matched the expected result.

**Screenshot:**

<img width="667" height="36" alt="image" src="https://github.com/user-attachments/assets/6a9b38d9-d096-46b2-a911-784ce393b918" />

**Experiment Without Lock:**

Removed the `with lock:` statement and ran the program several times. The final counter still displayed `200000` during my tests.

**Screenshot:**

<img width="656" height="106" alt="image" src="https://github.com/user-attachments/assets/213c48c3-7c35-438d-8a3c-2f2b6a06e0c1" />

This means both threads completed their increments correctly in my tests. However, race conditions may still happen when multiple threads access shared data without synchronization. The result can depend on the Python implementation and execution environment.

**Final Code:**

Restored the `with lock:` statement after the experiment.

**Screenshot:**

<img width="665" height="37" alt="image" src="https://github.com/user-attachments/assets/272f035b-859b-4810-b777-a1eede760c22" />

**Guide Questions and Answers:**

1. **What is a shared resource?**

   It is data or an object that can be accessed by multiple threads.

2. **What is a race condition?**

   It happens when multiple threads access or modify shared data at the same time, which may cause unexpected results.

3. **What is the purpose of `threading.Lock()`?**

   It prevents multiple threads from entering a protected section at the same time.

4. **What is a critical section?**

   It is the part of the program where shared data is accessed or modified.

5. **Why is synchronization important when multiple threads access shared data?**

   It helps prevent conflicts and keeps shared data correct and consistent.

## General Guide Questions and Answers

1. **What is the difference between a process and a thread?**

   A process is a running program, while a thread is a smaller unit of execution within a process.

2. **What are the advantages of using multithreading?**

   It allows a program to handle multiple tasks, improves responsiveness, and makes better use of resources.

3. **How does multithreading improve application responsiveness?**

   It allows an application to continue doing other tasks while another thread is busy.

4. **What is the difference between concurrency and parallelism?**

   Concurrency means multiple tasks make progress during the same period. Parallelism means multiple tasks execute at the same time.

5. **Why is a lock necessary when multiple threads access shared data?**

   A lock prevents multiple threads from modifying shared data at the same time and helps avoid race conditions.

6. **What might happen if a thread is not properly synchronized?**

   It may cause race conditions, incorrect results, or unexpected behavior.

7. **Can multiple threads execute simultaneously on a single-core processor? Explain.**

   They can run concurrently, but only one thread executes instructions on the single core at a time. The processor switches between threads.

8. **How does the operating system manage kernel-level threads?**

   The operating system schedules the threads, assigns processor time, and manages their execution.

## Learning Outcomes

- Create and execute threads.
- Demonstrate concurrent execution.
- Explain thread coordination.
- Apply locks to protect shared resources.

## Conclusion

In this laboratory, I learned how to create and manage threads using Python. I was able to understand how multiple threads execute concurrently, how `join()` helps control thread execution, and how locks protect shared resources. I also observed that removing synchronization does not always produce an incorrect result, but race conditions can still happen. Overall, this activity helped me understand the importance of multithreading and thread synchronization in programming.
