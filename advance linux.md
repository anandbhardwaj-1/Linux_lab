# Linux Process Management and Monitoring

Processes are running instances of programs. Linux provides many tools to **monitor, control, and limit** processes.  
This document covers commonly used commands and techniques.

---

## 1. List All Running Processes
```bash
ps aux
```
- **ps** → process status.  
- Shows a snapshot of processes at the time of execution.  
- **Fields explained**:
  - `USER` → owner of the process  
  - `PID` → process ID  
  - `%CPU` → CPU usage percentage  
  - `%MEM` → memory usage percentage  
  - `COMMAND` → command that started the process  


## 2. Display Process Tree
```bash
pstree -p
```
- Displays processes in **hierarchical/tree structure**.  
- Parent → Child relationships are visible.  
- `-p` → shows PID along with each process.  


## 3. Monitor Processes in Real Time
```bash
top
```
- Dynamic, real-time process monitoring tool.  
- Continuously updates CPU and memory usage.  
- Keys while inside `top`:
  - `k` → kill a process by PID  
  - `r` → renice a process  
  - `q` → quit  


## 4. Start a Process with Lower Priority
```bash
nice -n 10 sleep 300 &
```
- **Nice value** controls process scheduling priority.  
- Range: `-20` (highest priority) → `19` (lowest).  
- `sleep 300 &` runs in background for 300 seconds.  

**Use case:** Run a heavy job without affecting system responsiveness.

---

## 5. Change Priority of a Running Process
```bash
renice 5 -p <PID>
```
- Changes the priority of a process after it starts.  
- Example:
  ```bash
  renice 10 -p 1234
  ```
  lowers the priority of process 1234.

---

## 6. CPU Affinity (Bind Process to Specific CPU)
```bash
taskset -cp 0 <PID>
```
- Restricts a process to specific CPU cores.  
- Example:
  ```bash
  taskset -cp 0,1 1234
  ```
  Process `1234` runs only on CPUs 0 and 1.  

**Why useful?**  
- Performance tuning  
- Prevents one process from hogging all CPUs.

---

## 7. I/O Scheduling Priority
```bash
ionice -c2 -n7 -p <PID>
```
- Controls how a process accesses disk I/O.  
- Classes:
  - `1` → Real-time (highest priority)  
  - `2` → Best-effort (default)  
  - `3` → Idle (runs only when system is idle)  
- `-n` sets priority within class (0 = highest, 7 = lowest).  



## 8. Trace System Calls of a Process
```bash
strace -p <PID>
```
- Attaches to a process and logs all **system calls** it makes.  
- Useful for debugging issues like:
  - File not found  
  - Permission denied  
  - Network calls  

**Example:**  
```bash
strace ls
```
Shows all syscalls used by `ls`.

---

## 9. Find Process Using a Port
```bash
sudo lsof -i :8080
```
- Lists processes using TCP/UDP port 8080.  

Alternative:
```bash
sudo netstat -tulnp | grep 8080
```

**Use case:** Troubleshoot why a server port is busy.

---

## 10. Per-Process Statistics
```bash
pidstat -p <PID> 1
```
- Reports CPU, memory, and I/O usage per process.  
- `1` → update every second.  


## 11. Control Resources with cgroups
Linux Control Groups (cgroups) allow limiting CPU, memory, and I/O usage of processes.

### Create a cgroup
```bash
sudo cgcreate -g cpu,memory:/mygroup
```

### Limit CPU usage
```bash
echo 50000 | sudo tee /sys/fs/cgroup/cpu/mygroup/cpu.cfs_quota_us
```
- `50000` microseconds out of `100000` → limits to **50% of one CPU**.

### Add a process to the cgroup
```bash
echo <PID> | sudo tee /sys/fs/cgroup/cpu/mygroup/cgroup.procs
```

**Use case:** Prevent background jobs from consuming too many resources.

---

# 🔑 Summary

- **ps, pstree, top** → view running processes  
- **nice, renice** → control CPU scheduling priority  
- **taskset, ionice** → manage CPU/I/O priorities  
- **strace, lsof** → debug process behavior and network usage  
- **pidstat, cgroups** → advanced resource monitoring and limitation