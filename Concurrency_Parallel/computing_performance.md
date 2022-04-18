# Concurrency

A concurrent piece of software utilizes multiple flows of control to solve a problem. These flows of control might be implemented as multiple threads running within the context of a single process, or multiple cooperating processes running either on a single computer or multiple computers. Multiple flows of
control can also be implemented within a process using other techniques such as fibers or coroutines.

The central problem of concurrent programming is how to coordinate multiple readers and/or multiple writers of a shared data file, in such a way as to ensure predictable, correct results. At the heart of this problem is a special kind of race condition known as a data race, in which two or more flows of control “compete” to be the first to read, modify and write a chunk of shared data. The crux of the concurrency problem is to identify and eliminate data races.

# Parallelism

Parallel computer hardware can perform more than one task at a time. In constrast, serial computer hardware is capable of doing only one thing at a time.

1.  implicit parallelism 
2.  explicit parallelism

Implicit parallelism refers to the use of parallel hardware components within a CPU for the purpose of improving the performance of a single instruction stream. This is also known as instruction level parallelism (ILP), because the CPU executes instructions from a single stream (a single thread) but each instruction is executed with some degree of hardware parallelism. Examples of implicit
parallelism include:
• pipelining,
• superscalar architectures, and
• very long instruction word (VLIW) architectures.

Explicit parallelism refers to the use of duplicated hardware components within a CPU, computer or computer system, for the purpose of running more than one instruction stream simultaneously. In other words, explicitly parallel hardware is designed to run concurrent software more efficiently than would
be possible on a serial computing platform. The most common examples of
explicit parallelism are:
• hyperthreaded CPUs,
• multicore CPUs,
• multiprocessor computers,
• computer clusters,
• grid computing, and
• cloud computing.

# Task versus Data Parallelism

1. Task Parallelism

    When multiple heterogeneous operations are performed in parallel, we call this task parallelism. Performing animation calculations on one core while performing collosion checks on another would be an example of this form of parallelism.

2. Data Parallelism. 

    when a single operation is performed on multiple data items in parallel, it is called data parallelism. Calculating 1000 skinning matrices by running 250 matrix calculations on each of four cores would be an example of data parallelism.


# Flynn's Taxonomy

1. Single instruction, single Data (SISD)

    A single instruction stream operating on a single data stream.

2. Multiple Instruction, multiple Data (MIMD)

    Multiple instruction streams operating on multiple independent data streams.

3. Single Instruction, multiple Data (SIMD)

    A single instruction stream operating on multiple data streams (i.e., performing the same sequence of
operations on multiple independent streams of data simultaneously).

4. Multiple instruction, single data (MISD)

    Multiple instruction streams all operating on a single data stream. 

# Single and Multiple Data

1.  In a SISD architecture, a single ALU performs the multiply first, followed by the divide. 

2.  In a MIMD architecture, two ALUs perform operations in parallel, operating on two independent instructions streams.

3. The MIMD classification also applies to the case in which a single ALU processes two independent instructions streams via time-slicing.

4. In a MISD architecture, two ALUs process the same instruction stream (multiply first, followed by divide) and ideally produce identical results. ALU 1 acts as a “hot spare” for ALU 0 and vice-versa, meaning that if one of the ALUs experiences a failure, the system can seamlessly switch to the other.

# GPU Parallelism: SIMT

Single instruction multiple thread (SIMT) is essentially a hybrid between SIMD and MIMD, used
primarily in the design of GPUs. It mixes SIMD processing (a single instruc-tion operating on multiple data streams simultaneously) with multithreading (more than one instruction stream sharing a processor via time-slicing).

# Orthogonality of Concurrency and Parallelism

concurrent software doesn’t require parallel hardware, and parallel hardware isn’t only for running concurrent software. For example, a concurrent multithreaded program can run on a single, serial CPU
core via preemptive multitasking. Likewise, instruction level parallelism is intended to improve the performance of a single thread, and therefore benefits both concurrent and sequential software. So while they are closely related, concurrency and parallelism are really orthogonal concepts. As long as our system involves multiple readers and/or multiple writers of a shared data object, we have a concurrent system. Concurrency can be achieved via preemptive multitasking (on serial or parallel hardware) or via true parallelism (in which each thread executes on a distinct core)—the techniques we’ll learn in this chapter will be applicable either way.