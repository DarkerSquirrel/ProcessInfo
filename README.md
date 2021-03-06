## ProcessInfo

A small class to gather information about a Windows process, its threads and modules.
It supports both x86 and x64. Gathering information from a x64 process of a WOW64 process works aswell.

It gathers information using NtQuerySystemInformation, NtQueryInformationProcess and NtQueryInformationThread.

---

Use SetProcess to specifie a process. The handle needs PROCESS_VM_READ | PROCESS_QUERY_INFORMATION | PROCESS_QUERY_INFORMATION_LIMITED access rights.
It's recommended but not mandatory to call RefreshInformation when specifying a new process.

The following process related functions are available:
- GetPID
- GetPEB
- GetEntrypoint
- IsNative
- GetProcessInfo

---

Use FirstThread and NextThread to enumerate through all threads of the process. This works similar to Thread32First and Thread32Next.
Alternatively use SetThread to specify a thread by its identifier.

The following thread related functions are available and will return information about the current thread:
- GetThreadState
- GetThreadStartAddress
- IsThreadWorkerThread
- IsThreadInAlertableState (this function doesn't support x64 to wow64)
- GetThreadInfo

---

GetLdrEntry returns a pointer to the LDR_DATA_TABLE_ENTRY structure of the specified module in the PEB.
