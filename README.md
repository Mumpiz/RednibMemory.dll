# RednibMemory.dll





### Example
    // Usings
    
    using System.Diagnostics; // for Process
    using RednibMemory; // RednibMemory.dll


    ///Instanciate Rednib Dll
    
    RednibMemory.MemoryReader memReader = new RednibMemory.MemoryReader();
    
    
    // Open a process
    
    // get all running processes with the name "myProcess"
    Process[] processes = Process.GetProcessesByName("myProcess");
    // select the first occurrence of the process "myProcess" (there could be more processes with the same name)
    Process selectedProcess = processes[0];
    // open the process
    memReader.OpenProcess(selectedProcess);


    // Write to memory
    
    // An address you are interested in (for better use, you could define it in hexadecimal format and convert it to int)
    IntPtr pAddress = 65000;
    // a decimal value you want to write
    int intToWrite = 100;
    // converting "intToWrite" to bytes
    byte[] bytesToWrite = BitConverter.GetBytes(intToWrite);
    // writing to memory
    memReader.WriteMemory(pAddress, bytesToWrite);


    // Read memory
    // An address you are interested in (for better use, you could define it in hexadecimal format and convert it to int)
    IntPtr pAddress = 65000;
    uint bytesToRead = 4; // read 4 bytes
    byte[] buffer = memReader.ReadMemory(IntPtr pAddress, bytesToRead)
