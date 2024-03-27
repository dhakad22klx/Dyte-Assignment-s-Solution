# Dyte Hiring Challenge Submission

Implemented BenchmarkSample function in the most efficient way possible.

## Solution Approach (Description)

After understanding the code and problem, I identified operations to improve performance and efficiency. By leveraging my competitive programming skills, I realized that eliminating unnecessary function calls was a key strategy. This optimization process was straightforward once I grasped the problem and code structure.I have takend reference of BenchmarkRawUDP function and have made following changes :

- Instead of calling 'getTestMsg()' function for each reader for each writer function call, I am calling it one time that is for each writer function call.

- Instead of calling 'waitForReaders(readChan, b)' function for each writer function call, I am calling it after all writer function calls.

## Result i got as compared to BenchmarkRawUDP function (Baseline Implementation) are following in order : 

- Number of iterations per second -    >=3 times better.
- Time for processing each iteration - >=4 times better.
- Bytes allocated per iteration        >20 times better.
- Number of allocations per iteration- >=3 times better.

![Screenshot from 2024-03-27 23-04-31](https://github.com/dhakad22klx/Dyte-Hiring-Challenge-Solution/assets/87806512/77835a8d-5740-4477-8db5-5a89a108706b)

## Trade-off

Insted of sending different message 'buf' to all readers in each writer function call, now we are sending same message 'buf' to all readers in each writer function call to have less memory footprints.
