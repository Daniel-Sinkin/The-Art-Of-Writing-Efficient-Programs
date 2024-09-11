# The-Art-Of-Writing-Efficient-Programs
My notes made while  working through Fedor Pikus' book of the same name.

The code in the book can be found [here](https://github.com/PacktPublishing/The-Art-Of-Writing-Efficient-Programs).

# Notes
## Chapter 1: Introduction to Performance and Concurrency
* Efficiency means having little "waste", good allocation of resources and making use of all (or at least most) of the resources availiable in a CPU.
* Performance has always be defined with respect to some metric.
    * The common metric of "speed" can be better defined as the throughput, the amount of computations / unit of time the program does.
    * Alternatively we could also measure the "turnaround" time, i.e., how long it takes to finishes some particular task.
    * Another potentially important metric is energy consumption, for example for mobile phones.
    * If "going as fast as possible" is not necessarily important (like live translation of speech) but "hiccups" are very bad then we want to optimize the "latency tail"
        * The "latency tail" can be defined as the difference between when data is availiable and when it is processed.
        * This metric can be measured with a percentile (for example 95th percentile) of the latency. We try to optimize (95th percentile) / (mean percentile) (or median)
* "Good enough" exists when having to balance different metrics (you can always optimize energy efficiency).
* Efficiency and performance are roughly correlated, as not wasting CPU resources tends to improve performance and energy consumption.
* "Do not optimize prematurely", "yes, but do not pessimize intentionally either."
* The following are important for high performance:
    * Choosing the right algorithm
    * Using CPU resources effectively
    * Using memory effectively
    * Avoiding unnecessary computations
    * Using ocncurrency and multi-threading effectively
    * Using the programming language effectively, avoiding inefficiencies
    * Measuring performance and interpreting results

### Questions
1. Why is program performance important despite advances in processing power?
    * As raw compute power grows the needs also grow (author mentioned chip verification), if we want to keep going at the pace that we are going right now we needs strong performance aware software engineers to supplement the hardware engineering side, lest we get into stagnation, which nobody wants.
2. Why does understanding software perforamcne require low-level knowledge of teh computing hardware and programming languages?
    * If you don't know what you are instructing you can't do fine grained optimizations.
    * Not understanding your tools forces you to use very strong abstractions.
3. What is the difference between performance and efficiency?
    * Efficiency cares about optimal allocation of resources without some metric to optimize, performance is always interesting in optimize a particular metric.
    * Efficiency itself is never an end goal, it only serves as a tool to achieve performance (for example less waste -> more throughput -> less runtime -> less energy consumption)
4. Why must performance be defined with respect to specific metrics?
    * Can't optimize what you can't measure.
5. How can we judge whether the performance-related goals for specific metrics are accomplished?
    * Define a metric, measure it and evaluate results.

## Chapter 2: Performance Measurements
* The first question is never "how do we optimize?"
    * The first question should be "do we have to optimize?"
    * The second question is "what do we optimize?"
* It is an unavoidable problem that when we measure things the results get modified.
    * Running a profiler slows the program down, but the relative performance should remain stable, if the profiler is working correctly.
* When we locate something that 

### Questions
1. Why are performance measurements necessary?
2. Why do we need so many different ways to measure performance?
3. What are the advantages and limitations of manual benchmarking?
4. How is profiling used to measure performance?
5. What are the uses of small-scale benchmarking, including micro-benchmarks?

## Chapter 3: CPU Architecture, Resources, and Performance

### Questions
1. What is the key to using the CPU resources efficiently?
2. How can we use instruction-level parallelism to improve performance?
3. How can the CPU execute computations in parallel if the latter one needs the results of the former one?
    * It could guess the result of the previous one and run that
    * If there are a small amount of possible results it could compute all possibilites and discard them later
4. Why are conditional branches much more expensive than simply the cost of evaluating a conditionnal expresion?
5. What is speculative execution?
6. What optimization techniques are available to improve the ffectiveness of pipelining in code with conditional computations?

## Chapter 4: Memory Architecture and Performance

### Questions
1. What is the memory gap?
2. What factors affect the observed memory speed?
3. How can we find the places in the program where accessing memory is the main cause of poor performance?
4. What are the main ways to optimize the program for better memory performance?

## Chapter 5: Threads, Memory, and Concurrency

### Questions
1. What is the memory model?
2. Why is access to the shared data so important to understand?
3. What determines the overall memory model for a program?
4. What constraints the performance gain from concurrency?

## Chapter 6: Concurrency and Performance

### Questions
1. What are the defining properties of lock-based, lock-free, and wait-free programs?
2. If an algorithm is wait-fre, does it mean that it will scale perfectly?
3. What are the drawbacks of the locks that prompt us to look for alternatives?
4. What is the difference between a shared counter and a shared index into an array or another container?
5. What is the key advantage of the publishing protocol?

## Chapter 7: Data Structures for Concurrency

### Questions
1. What is the most critical feature of the interface of data structures designed for thread safety?
2. Why are the data structures with limited functionality often more fficinet than their generic variants?
3. Are lock-free data structures always faster than the lock-based ones?
4. What are the challenges of managing memory in concurrentapplicaitons?
What is the A-B-A problem?

## Chapter 8: Concurrency in C++

### Questions
1. Why is the foundation of concurrent programming laid in C++11 important?
2. How do we use parallel STL algorithms?
3. What are coroutines?

## Chapter 9: High-Performance C++

### Questions
1. When is passing even large objects by value acceptable?
2. When using resource-owning smart pointers, how should we invoke functions that operate on the objects?
3. What is the return value optimization, and where is it used?
4. Why does inefficient memory management affect not just memory consumption but also runtime?
5. What is the A-B-A problem?

## Chapter 10: Compiler Optimizations in C++

### Questions
1. What constraints the compiler optimizations?
2. Why is function inlining so important for compiler optimizations?
3. Why doesn't the compiler make an obvious optimization?
4. Why is inlining an effective optimization?

## Chapter 11: Undefined Behavior and Performance

### Questions
1. What is undefined behavior?
2. Why can't we define the results for any situation the program may encounter?
3. If I write code the standard labels as UB, test the result, and verify that the code works, I'm OK, right?
4. Why would I want to intentionally design a program that has documented undefined behavior?

## Chapter 12: Design for Performance

### Questions
1. What is design for performance?
2. How do we make sure that the interfaces do not restrict optimal implementation?
3. Why do interfaces that communicate the client's intent allow for better performance?
4. How can we make informed performance-related design decisions whne we have no performance measurements?

# Attributions
This was forked from [here](https://github.com/PacktPublishing/The-Art-of-Writing-Efficient-Programs)