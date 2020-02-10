# cpuAgent credit exam

Your task is to implement 2 applications:
- Dashboard server that aggregates the CPU metrics
- Agent that is installed on monitored computers which collects CPU usage and sends the data to the Dashboard server 

## Dashboard Server
Server is waiting for commands to be posted to `STDIN`. Available commands:
- `show` – displays the current data. The display format is the following:
    ```
    Address | CPU usage (%) | Critical
    ----------------------------------
    127.0.0.1 | 25.56 | No
    ...
    ```

    `Critical` threshold is `80%`.
- `show-critical` - shows only `critical` entries
- `show-history {addr} {n}` - shows last `{n}` entries for server with address `{addr}` in the following format: 
    ```
    {timestamp} : {value} 
    ```

## agent
Program that collects CPU usage by parsing the output of the `top -bn1 1` command and then sends it back to the Dashboard
server. The data collection takes place every 5 second.
