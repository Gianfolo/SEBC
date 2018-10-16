- The memory for the OS is too high and we adjust the multiply factor from 0.1 to 0.05. The problem is that this value shouldn't be absolute, because it depends also on the size of the machine. For smaller machines, probably the factor 0.1 is correct.
The resulting value for OS memory is about 6 GB.

- The workload factor affects the number of mapper/reducers used in map/reduce job: higher the value, higher the parallelism used within the job, that means that more cores are used by the job. With the selected servers the acceptable values are 1,2: there no sufficient cores to use higher values.

