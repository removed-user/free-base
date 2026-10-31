
| Tool Name | Functional Category | Purpose & Focus | Why it is missing from sbase/ubase/coreutils |
| :--- | :--- | :--- | :--- |
| **`lsblk`** | Storage Mechanics | Lists all available or specified block devices in a clear tree layout. | Queries the modern Linux `/sys/dev/block` API directly; too modern/specific for `ubase`. |
| **`blkid`** | Storage Mechanics | Locates and prints block device attributes (UUIDs, filesystem labels). | Relies heavily on `libblkid` to parse disk headers; ignored by simple bases. |
| **`findmnt`** | Storage Mechanics | Search tool for finding mounted filesystems and parsing mount parameters. | Reads `/proc/self/mountinfo`, which tracks highly volatile, non-POSIX Linux mount states. |
| **`wipefs`** | Storage Mechanics | Wipes filesystem, raid, or partition-table signatures from a device. | Destructive low-level disk plumbing utility; completely outside the scope of `coreutils`. |
| **`fstrim`** | Storage Mechanics | Discards unused blocks on a mounted filesystem (SSD TRIM operation). | Direct interface to the Linux `FITRIM` ioctl; relies on a running filesystem context. |
| **`unshare`** | Namespace Controls | Runs a program with some namespaces unshared from its parent process. | Relies on the highly specific, non-portable Linux `unshare()` system call. |
| **`nsenter`** | Namespace Controls | Enters the namespaces of another running process (vital for containers). | Requires direct interaction with Linux `/proc/[pid]/ns/` file descriptors. |
| **`prlimit`** | Namespace Controls | Dynamically fetches or sets the hard/soft resource limits of a process. | Wraps the Linux-specific `prlimit64()` system call, allowing targeted PID manipulation. |
| **`setpriv`** | Namespace Controls | Runs a program with a clean, fine-tuned set of Linux kernel privileges. | Handles complex Linux-specific bits like NoNewPrivs and capability bounding sets. |
| **`ionice`** | Namespace Controls | Sets or gets the explicit disk I/O scheduling class and priority for a task. | Tied strictly to the Linux kernel CFQ/BFQ block layer I/O schedulers. |
| **`lscpu`** | Hardware Querying | Gathers and formats detailed CPU architecture, core, and cache topologies. | Parsetree engine for `/sys/devices/system/cpu/`; too specific for a generic base system. |
| **`lsipc`** | Hardware Querying | Extracts details on active Inter-Process Communication facilities. | Reads system IPC states (`shm`, `sem`, `msg`) via Linux-specific proc files. |
| **`lsmem`** | Hardware Querying | Inspects the layout and state of available online/offline physical memory. | Interacts exclusively with the Linux memory hotplug subsystem interfaces under `/sys`. |
| **`lslocks`** | Hardware Querying | Lists all active local file locks held by system processes. | Parses `/proc/locks`, which exposes Linux kernel internal tracking data structures. |
| **`flock`** | Terminal / Scripting | Manages clean advisory file locks from inside shell scripts. | Implements logic around the `flock()` syscall to prevent race conditions in scripts. |
| **`script`** | Terminal / Scripting | Makes a clean typescript recording of everything printed to a terminal. | Spawns a pseudo-terminal (`pty`) session to mirror and log bidirectional data streams. |
| **`uuidgen`** | Terminal / Scripting | Generates a standard universally unique identifier (UUID) string. | Relies on reading high-entropy data from `/dev/urandom` alongside standard formatting. |
| **`setarch`** | Terminal / Scripting | Alters the reported architecture layout in a new program environment. | Wraps the Linux `personality()` system call to trick binaries (e.g., x86_64 pretending to be i686). |
