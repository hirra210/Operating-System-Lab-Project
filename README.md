Mini OS Simulator: Integrated Process Management System
Project Overview
The Mini OS Simulator is a comprehensive C++ application designed to emulate the core functional components of a modern operating system. Developed as a solution to the "Complex Computing Problem" (CCP), this project bridges the gap between theoretical operating system concepts and practical low-level implementation. The primary objective is to simulate how an OS manages process lifecycles, synchronizes concurrent tasks, and ensures safe resource allocation in a multi-threaded environment.

Core Functionalities
The simulator integrates three distinct yet interconnected modules to replicate a functioning OS kernel:

Dynamic CPU Scheduling: The system features an intelligent scheduling engine that adapts its algorithm based on real-time workload intensity. For lighter loads (5 processes or fewer), the system utilizes Non-Preemptive Priority Scheduling, which selects tasks based on assigned priority to minimize context switching overhead. However, when the system load increases beyond this threshold, it automatically transitions to a Round Robin algorithm (Time Quantum = 2). This dynamic switch ensures fairness and responsiveness, effectively preventing process starvation in high-density environments.

Concurrency & Synchronization: The project implements the classic Producer-Consumer problem to handle process generation and execution. "Producer" threads dynamically create processes and place them into a bounded buffer, while "Consumer" threads retrieve them for execution. Crucially, this implementation avoids inefficient busy-waiting by utilizing counting semaphores and mutex locks. This ensures thread safety, prevents race conditions, and guarantees that the buffer is accessed atomically.

Deadlock Prevention: To guarantee system stability, the simulator incorporates Dijkstra’s Banker’s Algorithm. Before any process is admitted to the CPU or granted resources, the system evaluates the safety of the allocation. If granting resources would lead to an unsafe state (potential deadlock), the process is blocked. This proactive approach ensures the system acts conservatively to maintain a secure state at all times.

Technical Architecture
Built entirely in C++, the simulator leverages the standard <thread> and <mutex> libraries to simulate real-time parallel execution. The code is structured with a modular architecture, keeping the Process Manager, Scheduler, and Safety Algorithms as distinct components. This modularity not only demonstrates clean software engineering principles but also provides a clear visualization of the intricate balancing act performed by operating systems.

