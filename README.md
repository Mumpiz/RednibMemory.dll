# RednibMemory.dll

### Overview
    // RednibMemory.dll
    using RednibMemory
    // (to use Process you must include "System.Diagnostics")
    

    // Get/Set current process (you wont need it, hower you could use it)
    public Process CurrentProcess {get; set;}
    
    // returns true if it has a handle to a process, otherwise false
    public bool HasHandle()
    
    // opens the passed process
    public void OpenProcess(Process processToRead)
    
    // closes the currently opened handle
    public void CloseHandle()
    
    // reads memory at address "memoryAddress" with size "bytesToRead"
    public byte[] ReadMemory(IntPtr memoryAddress, uint bytesToRead)
    
    // writes to memory at "memoryAddress" the bytes "bytesToWrite"
    public void WriteMemory(IntPtr memoryAddress, byte[] bytesToWrite)



### Example
    // Usings
    
    using System.Diagnostics; // for Process
    using RednibMemory; // RednibMemory.dll


    ///Instanciate Rednib Dll
    
    RednibMemory.MemoryReader memReader = new RednibMemory.MemoryReader();
    
    
    // Open a process
    
    // get all running processes with the name "myProcess"
    Process[] processes = Process.GetProcessesByName("myProcess");
    // select the first occurrence of the process "myProcess"
    // (there could be more than one process with the same name)
    Process selectedProcess = processes[0];
    // open the process
    memReader.OpenProcess(selectedProcess);


    // Write to memory
    
    // An address you are interested in (for better use, you could define it in hexadecimal format and convert it to int)
    int pAddress = 65000;
    // a value you want to write
    int intToWrite = 100;
    // converting "intToWrite" to bytes
    byte[] bytesToWrite = BitConverter.GetBytes(intToWrite);
    // writing to memory (casting pAddress to IntPtr)
    memReader.WriteMemory((IntPtr)pAddress, bytesToWrite);


    // Read memory
    // An address you are interested in (for better use, you could define it in hexadecimal format and convert it to int)
    IntPtr pAddress = 65000;
    uint bytesToRead = 4; // read 4 bytes
    byte[] buffer = memReader.ReadMemory(IntPtr pAddress, bytesToRead)
