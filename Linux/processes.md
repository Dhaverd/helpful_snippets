# Process interaction snippets

## Find process occupying port

```bash
ss -lptn 'sport = :5173'
```

### Output example:

```bash
State                 Recv-Q                Send-Q                               Local Address:Port                                 Peer Address:Port                Process                                          
LISTEN                0                     511                                          [::1]:5173                                         [::]:*                    users:(("node",pid=29634,fd=32))
```

## Kill process

```bash
sudo kill -[signal] [PID]
```

### Example:

```bash
sudo kill -9 29634
```

### Signals:
- **SIGTERM (Signal 15).** This signal asks for a process to terminate. The process can capture this signal, perform cleanup operations, and then exit. By default, the kill command sends SIGTERM if no other signal is specified.

- **SIGKILL (Signal 9).** It forcefully kills a process. The process cannot capture or ignore this signal, which results in an immediate termination. It should be used as a last resort when a process doesn’t respond to SIGTERM.

- **SIGINT (Signal 2).** This is typically sent when you press Ctrl + C in the terminal. It interrupts a process and is usually used to stop a process running in the foreground.

- **SIGHUP (Signal 1).** Sent to a process when its controlling terminal is closed and often used to reload configuration files.

- **SIGQUIT (Signal 3).** Causes a process to terminate and produce a core dump file for debugging.

- **SIGSTOP (Signal 19).** Pauses a process without killing it, similar to pressing Ctrl + Z in the terminal.

- **SIGCONT (Signal 18).** Continues a process that was stopped by SIGSTOP or Ctrl + Z.