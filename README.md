**POOLPROCESS.PY**
There are 4 worker processes, each handling a subset of numbers.
Example:
Process 1 → 0,1,2,…
Process 2 → next subset … etc.
All 4 processes run concurrently on different CPU cores (if available).
This speeds up CPU-bound tasks compared to sequential execution.

**PROCESSBARRIER.PY**
p1 and p2 reach synchronizer.wait() → both wait for each other.
Once both are ready → barrier is released → both continue almost at the same time.
serializer ensures only one prints at a time, avoiding garbled output.
p3 and p4 run independently → print without waiting.
Overall, output shows barrier-synchronized and unsynchronized processes.

**NO BACKGROUND PROCESS.PY**
background_process starts:
Prints Starting background_process
Prints 0 → 4
Sleeps 1 second
Prints Exiting background_process
NO_background_process starts:
Prints Starting NO_background_process
Prints 5 → 9
Sleeps 1 second
Demonstrates process-based parallelism using multiprocessing.Process.
Each process executes the same function (foo) but behaves differently based on process name.
Both processes run concurrently, so output can be interleaved.
Non-daemon processes ensure the main program waits for them to finish.
sleep(1) simulates time-consuming tasks.

**SWAPINGPROCESS.PY**
For i = 0 → 5:
Create process for myFunc(0) → start → wait until it finishes.
Create process for myFunc(1) → start → wait until it finishes.
Repeat until i = 5
Creates 6 separate processes to run myFunc with arguments 0–5.
Each process runs sequentially, not concurrently, due to join() after start().
To run all 6 processes concurrently, you should:

Prints Exiting NO_background_process

Both processes run concurrently, so the order of outputs may mix.
