# RednibMemory.dll

### Requirements
    using System.Diagnostics; // for Process
    using RednibMemory; // RednibMemory.dll

### Instanciate my Rednib Dll
    RednibMemory.MemoryReader memReader = new RednibMemory.MemoryReader();
    
### Open a process
    // get all running processes with the name "myProcess"
    Process[] processes = Process.GetProcessesByName("myProcess");
    // select the first occurrence of the process "myProcess" (there could be more processes with the same name)
    Process selectedProcess = processes[0];
    // open the process
    memReader.OpenProcess(selectedProcess);

### Write to memory
    IntPtr pAddress = ...;
    byte[] bytesToWrite = ...;
    memReader.WriteMemory(pAddress, bytesToWrite);

### Read memory
    uint bytesToRead = 4; // read 4 bytes
    byte[] buffer = memReader.ReadMemory(IntPtr pAddress, bytesToRead)
