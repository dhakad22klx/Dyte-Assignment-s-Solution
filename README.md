# Dyte Hiring Challenge Submission

Implemented BenchmarkSample function in the most efficient way possible.

## Solution Approach (Description)

After understanding the code and problem, I identified operations to improve performance and efficiency to some extent. By leveraging my programming skills, I realized that some precomputation may be useful.I have taken reference of BenchmarkRawUDP function and have made following changes :

- Precomputing connections instead of building connection for each writer function call (i.e. b.N times).

- Instead of sending UDP packets sequencially now we are sending concurrently utilizing goroutines.

## Result i got as compared to BenchmarkRawUDP function (Baseline Implementation) are following in order : 

- Number of iterations per second -    Almost 2 times better.
- Time for processing each iteration - Almost  1.5 times better.
- Bytes allocated per iteration       - Bit better.
- Number of allocations per iteration - Bit better.

![Screenshot from 2024-03-30 23-43-14](https://github.com/dhakad22klx/Dyte-Hiring-Challenge-Solution/assets/87806512/e6901148-fbf1-4003-92af-b8f143e29d94)

## Trade-offs

- We are not caring about the order in which each reader receiving messages.
- Increased resource usage, as each thread requires its own set of resources such as memory and CPU time.
-  Precomputing the connection pool improves performance by reducing latency since connections are established beforehand. However, Preallocation of resources may not be suitable for scenarios where the number of connections ( readersCount ) varies dynamically.
