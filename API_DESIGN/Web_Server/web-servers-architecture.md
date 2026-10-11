<!-- # Web Servers & CPU Architecture Notes

## 1. Hardware Basics: Cores, Threads, and Processes
*   **CPU Core:** A core is the physical unit in a CPU that performs tasks[cite: 6]. Single-core CPUs execute one instruction at a time, while multi-core CPUs allow parallel execution of tasks[cite: 6].
*   **Thread:** A thread is a virtual core that divides a physical core's capacity[cite: 6]. Technologies like Hyper-Threading (HT) or Simultaneous Multithreading (SMT) allow a single core to handle multiple threads simultaneously[cite: 6].
*   **Process:** A process is a program currently running on the computer[cite: 6]. It operates within an independent execution context and has its own memory space[cite: 6]. 
*   **Thread vs. Process:** Threads share the memory of the process they belong to, while processes communicate via Inter-process communication (IPC)[cite: 6].
*   **CPU Performance:** Performance is calculated by multiplying the Clock Speed (GHz) by the IPC (Instructions per Clock)[cite: 6]. 

## 2. Web Server Fundamentals
*   **Definition:** A web server consists of hardware and software that uses protocols like HTTP to respond to client requests[cite: 6]. Popular examples include Apache, Nginx, Microsoft IIS, and Caddy[cite: 6].
*   **Static vs. Dynamic Content:** 
    *   Static content refers to unchanged files delivered directly, such as HTML, CSS, JavaScript, and images[cite: 6].
    *   Dynamic content requires backend processing based on user interaction, such as user dashboards, live data updates, and authentication[cite: 6].
*   **Key Features:** Web servers are responsible for serving static files, processing dynamic content, logging, security (SSL/TLS), load balancing, and caching[cite: 6].

## 3. Server Architectures
*   **Single-Threaded Servers:** These servers use one execution thread to handle all requests[cite: 6]. They manage concurrent connections using non-blocking, event-driven operations (like Node.js) and context switching[cite: 6].
    *   *Context Switching:* The OS rapidly pauses one task, saves its state, and loads another, making it appear as if tasks are running simultaneously[cite: 6].
    *   *Limitation:* CPU-intensive tasks or blocking I/O operations will block the main thread, forcing all other requests to wait[cite: 6].
*   **Multi-Threaded Servers:** These servers assign incoming requests to separate threads, allowing truly parallel execution[cite: 6].
    *   *Limitation:* They require complex synchronization mechanisms (locks, mutexes) to prevent race conditions (inconsistent data modifications) and deadlocks[cite: 6].

## 4. Execution Models
*   **Synchronous vs. Asynchronous:**
    *   *Synchronous:* Operations are blocking; the thread waits idly for a task (like a file read) to finish before moving on[cite: 6].
    *   *Asynchronous:* Operations are non-blocking; the thread continues executing other tasks while waiting for the background operation to complete[cite: 6].
*   **Concurrency vs. Parallelism:**
    *   *Concurrency:* Multiple tasks overlap in time, often managed by time-slicing on a single core or an event loop[cite: 6].
    *   *Parallelism:* Tasks execute at the exact same time on different CPU cores[cite: 6].
*   **Multiprocessing:** This allows programs to use multiple CPU cores to run independent processes in parallel[cite: 6]. This avoids race conditions because each process has its own memory[cite: 6].

## 5. How Node.js Handles Threads
*   **Single-Threaded Execution:** Node.js executes standard JavaScript code on a single main thread called the event loop[cite: 6].
*   **Internal Multi-Threading:** Node.js utilizes a libuv thread pool in the background to prevent blocking the main thread during specific I/O-bound tasks[cite: 6].
*   **Thread Pool Use Cases:** Node.js offloads file system operations (`fs.readFile`), DNS lookups, cryptographic operations (hashing), and data compression (`zlib`) to this internal thread pool[cite: 6]. -->