# CPU-Scheduling-
in single processor
# What is CPU Scheduling?
CPU scheduling is a process which allows one process to use the CPU while the execution of another process is on hold(in waiting state) due to unavailability of any resource like I/O etc, thereby making full use of CPU. The aim of CPU scheduling is to make the system efficient, fast and fair.

Whenever the CPU becomes idle, the operating system must select one of the processes in the ready queue to be executed. The selection process is carried out by the short-term scheduler (or CPU scheduler). The scheduler selects from among the processes in memory that are ready to execute, and allocates the CPU to one of them.
# CPU Scheduling: Dispatcher
Another component involved in the CPU scheduling function is the Dispatcher. The dispatcher is the module that gives control of the CPU to the process selected by the short-term scheduler. This function involves:

Switching context
Switching to user mode
Jumping to the proper location in the user program to restart that program from where it left last time.
The dispatcher should be as fast as possible, given that it is invoked during every process switch. The time taken by the dispatcher to stop one process and start another process is known as the Dispatch Latency. Dispatch Latency can be explained using the below figure:

Dispatch latency of Process Dispatcher

# Types of CPU Scheduling
CPU scheduling decisions may take place under the following four circumstances:

When a process switches from the running state to the waiting state(for I/O request or invocation of wait for the termination of one of the child processes).
When a process switches from the running state to the ready state (for example, when an interrupt occurs).
When a process switches from the waiting state to the ready state(for example, completion of I/O).
When a process terminates.
In circumstances 1 and 4, there is no choice in terms of scheduling. A new process(if one exists in the ready queue) must be selected for execution. There is a choice, however in circumstances 2 and 3.

When Scheduling takes place only under circumstances 1 and 4, we say the scheduling scheme is non-preemptive; otherwise the scheduling scheme is preemptive.


 
# Non-Preemptive Scheduling
Under non-preemptive scheduling, once the CPU has been allocated to a process, the process keeps the CPU until it releases the CPU either by terminating or by switching to the waiting state.

This scheduling method is used by the Microsoft Windows 3.1 and by the Apple Macintosh operating systems.

It is the only method that can be used on certain hardware platforms, because It does not require the special hardware(for example: a timer) needed for preemptive scheduling.

# Preemptive Scheduling
In this type of Scheduling, the tasks are usually assigned with priorities. At times it is necessary to run a certain task that has a higher priority before another task although it is running. Therefore, the running task is interrupted for some time and resumed later when the priority task has finished its execution.

# CPU Scheduling: Scheduling Criteria
There are many different criterias to check when considering the "best" scheduling algorithm, they are:

# CPU Utilization
To make out the best use of CPU and not to waste any CPU cycle, CPU would be working most of the time(Ideally 100% of the time). Considering a real system, CPU usage should range from 40% (lightly loaded) to 90% (heavily loaded.)

# Throughput
It is the total number of processes completed per unit time or rather say total amount of work done in a unit of time. This may range from 10/second to 1/hour depending on the specific processes.

# Turnaround Time
It is the amount of time taken to execute a particular process, i.e. The interval from time of submission of the process to the time of completion of the process(Wall clock time).

# Waiting Time
The sum of the periods spent waiting in the ready queue amount of time a process has been waiting in the ready queue to acquire get control on the CPU.

# Load Average
It is the average number of processes residing in the ready queue waiting for their turn to get into the CPU.

# Response Time
Amount of time it takes from when a request was submitted until the first response is produced. Remember, it is the time till the first response and not the completion of process execution(final response).

In general CPU utilization and Throughput are maximized and other factors are reduced for proper optimization.
# First Come First Serve Scheduling
In the "First come first serve" scheduling algorithm, as the name suggests, the process which arrives first, gets executed first, or we can say that the process which requests the CPU first, gets the CPU allocated first.

First Come First Serve, is just like FIFO(First in First out) Queue data structure, where the data element which is added to the queue first, is the one who leaves the queue first.
This is used in Batch Systems.
It's easy to understand and implement programmatically, using a Queue data structure, where a new process enters through the tail of the queue, and the scheduler selects process from the head of the queue.
A perfect real life example of FCFS scheduling is buying tickets at ticket counter.

# Problems with FCFS Scheduling
Below we have a few shortcomings or problems with the FCFS scheduling algorithm:

It is Non Pre-emptive algorithm, which means the process priority doesn't matter.
If a process with very least priority is being executed, more like daily routine backup process, which takes more time, and all of a sudden some other high priority process arrives, like interrupt to avoid system crash, the high priority process will have to wait, and hence in this case, the system will crash, just because of improper process scheduling.

Not optimal Average Waiting Time.
Resources utilization in parallel is not possible, which leads to Convoy Effect, and hence poor resource(CPU, I/O etc) utilization.

# What is Convoy Effect?
Convoy Effect is a situation where many processes, who need to use a resource for short time are blocked by one process holding that resource for a long time.

This essentially leads to poort utilization of resources and hence poor performance.
# Shortest Job First(SJF) Scheduling
Shortest Job First scheduling works on the process with the shortest burst time or duration first.

This is the best approach to minimize waiting time.
This is used in Batch Systems.
It is of two types:
1)Non Pre-emptive
2)Pre-emptive
To successfully implement it, the burst time/duration time of the processes should be known to the processor in advance, which is practically not feasible all the time.
This scheduling algorithm is optimal if all the jobs/processes are available at the same time. (either Arrival time is 0 for all, or Arrival time is same for all)
# Problem with Non Pre-emptive SJF
If the arrival time for processes are different, which means all the processes are not available in the ready queue at time 0, and some jobs arrive after some time, in such situation, sometimes process with short burst time have to wait for the current process's execution to finish, because in Non Pre-emptive SJF, on arrival of a process with short duration, the existing job/process's execution is not halted/stopped to execute the short job first.

This leads to the problem of Starvation, where a shorter process has to wait for a long time until the current longer process gets executed. This happens if shorter jobs keep coming, but this can be solved using the concept of aging.
# Round Robin Scheduling
A fixed time is allotted to each process, called quantum, for execution.
Once a process is executed for given time period that process is preemptied and other process executes for given time period.
Context switching is used to save states of preemptied processes.
# Multilevel Queue Scheduling
Another class of scheduling algorithms has been created for situations in which processes are easily classified into different groups.

For example: A common division is made between foreground(or interactive) processes and background (or batch) processes. These two types of processes have different response-time requirements, and so might have different scheduling needs. In addition, foreground processes may have priority over background processes.

A multi-level queue scheduling algorithm partitions the ready queue into several separate queues. The processes are permanently assigned to one queue, generally based on some property of the process, such as memory size, process priority, or process type. Each queue has its own scheduling algorithm.

For example: separate queues might be used for foreground and background processes. The foreground queue might be scheduled by Round Robin algorithm, while the background queue is scheduled by an FCFS algorithm.


 
In addition, there must be scheduling among the queues, which is commonly implemented as fixed-priority preemptive scheduling. For example: The foreground queue may have absolute priority over the background queue.


Let us consider an example of a multilevel queue-scheduling algorithm with five queues:

System Processes
Interactive Processes
Interactive Editing Processes
Batch Processes
Student Processes
Each queue has absolute priority over lower-priority queues. No process in the batch queue, for example, could run unless the queues for system processes, interactive processes, and interactive editing processes were all empty. If an interactive editing process entered the ready queue while a batch process was running, the batch process will be preempted.
# Multilevel Feedback Queue Scheduling
In a multilevel queue-scheduling algorithm, processes are permanently assigned to a queue on entry to the system. Processes do not move between queues. This setup has the advantage of low scheduling overhead, but the disadvantage of being inflexible.

Multilevel feedback queue scheduling, however, allows a process to move between queues. The idea is to separate processes with different CPU-burst characteristics. If a process uses too much CPU time, it will be moved to a lower-priority queue. Similarly, a process that waits too long in a lower-priority queue may be moved to a higher-priority queue. This form of aging prevents starvation.

Multi Level Feedback Scheduling Queues

An example of a multilevel feedback queue can be seen in the below figure.


 

In general, a multilevel feedback queue scheduler is defined by the following parameters:

The number of queues.
The scheduling algorithm for each queue.
The method used to determine when to upgrade a process to a higher-priority queue.
The method used to determine when to demote a process to a lower-priority queue.
The method used to determine which queue a process will enter when that process needs service.
The definition of a multilevel feedback queue scheduler makes it the most general CPU-scheduling algorithm. It can be configured to match a specific system under design. Unfortunately, it also requires some means of selecting values for all the parameters to define the best scheduler. Although a multilevel feedback queue is the most general scheme, it is also the most complex.


