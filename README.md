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
### Questions
1. Why are performance measurements necessary?
2. Why do we need so many different ways to measure performance?
3. What are the advantages and limitations of manual benchmarking?
4. How is profiling used to measure performance?
5. What are the uses of small-scale benchmarking, including micro-benchmarks?


# Attributions
This was forked from [here](https://github.com/PacktPublishing/The-Art-of-Writing-Efficient-Programs)