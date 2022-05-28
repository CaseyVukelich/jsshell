# JavaScript Shell
A shell written in NodeJS

# Run
```script
chmod +x shell
./shell
```
# About
When a command is entered into the shell, it will first check if the command is a builtin.
If not, then it will spawn a child process for the job.
The new process is NOT a NodeJS instance. For this reason, only one job at a time is supported as explained below.
Planned future versions would spanw new jobs as NodeJS instances running this JS shell to support multiple jobs.
^C and ^Z keyboard interrupts are forwarded to the command.

# Important details about NodeJS and IPC channels
NodeJS only supports IPC channels to child processes which are also instances of NodeJS.
In most cases communication over an IPC channel to non-NodeJS child processes does work, some commands do trigger unexpected results.
When a non-NodeJS child process is closed, the IPC channel is not always freed.

# Builtin commands
```script
cd [directory]      - change working directory to the specified location
echo [-n] [arg...]  - print to STDOUT (-n to interpret newline characters)
exit                - exit the shell
fg                  - bring a backgrounded process into the foreground
help                - display help message
jobs                - list all stopped jobs
pwd                 - print current working directory
```
