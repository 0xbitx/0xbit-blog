
<p align="center">
<img src="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExempiaWZvd3ptcmN6cW5ncmRsNG1teTU2YnI3ejluczdrNjd3bWhxaCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3o6ZsUk0jb6m80uAg0/giphy.webp", width="300", height="300">
</p>

<h1 align="center"> PROC-HACKER </h1>

<p align="center">
  <b>Linux based process analyzer for hackers.</b>
</p>

### DESCRIPTION

PROC-HACKER is a Linux-based command-line tool designed to provide comprehensive and detailed insights into system processes. It displays a wide range of process details, including CPU usage, memory consumption, open files, network connections, thread information, and more. This tool is incredibly useful for developers, system administrators, security professionals, and digital forensics experts who need in-depth visibility and control over running processes. With its hierarchical tree-like display, PROC-HACKER makes it easy to trace parent-child relationships and understand the behavior and impact of each process on the system.

PROC-HACKER also includes advanced features to catch malware or malicious code hiding within legitimate processes. It can detect and expose malicious activities, such as unauthorized file access and suspicious network connections, providing a clear view of potential threats. This makes PROC-HACKER an invaluable tool for identifying and mitigating security risks on Linux systems.

In addition, PROC-HACKER offers an option to check files for malware using a hash table. By comparing the files' hashes against a database of known malware checksums, it can quickly identify and flag malicious files, enhancing the security and integrity of your system.

Additionally, PROC-HACKER offers two monitoring options:

    Snapshot Monitoring: Capture a snapshot of the current state of system processes.
    Realtime Monitoring: Continuously monitor system processes in real-time, updating the display based on user-provided intervals.

These monitoring options provide flexibility in how users can track and analyze process activities, making PROC-HACKER a versatile tool for both immediate and ongoing process investigation.
### Feature List
  Process Information
  
      Process Name: The name of the process.
      PID: The Process ID.
      Parent ID: The Parent Process ID.
      Command: The command line used to start the process.
      Executable Path: The path to the executable file of the process.
      User: The username of the process owner.
      CPU Times: The amount of time the process has spent in user and system mode.
      Memory Info: Resident Set Size (RSS) and Virtual Memory Size (VMS).
      Start Time: The time when the process started.
      Current Working Directory: The current working directory of the process.
  
  Open Files
  
      File Path: The path of the open file.
      File Descriptor (System Reference Number): The file descriptor used by the system to reference the open file.
      File Type: The type of the file (e.g., Python script, ELF binary, text file).
      File Size: The size of the file in bytes.
      Creation Time: The time when the file was created.
      Modification Time: The time when the file was last modified.
      Access Time: The time when the file was last accessed.
      MD5 checksum: checksum of a file.
  
  Network Connections
  
      Local Address: The local IP address and port.
      Remote Address: The remote IP address and port.
      Status: The status of the connection (e.g., ESTABLISHED, LISTEN).
  
  Child Processes
  
      Process Name: The name of the child process.
      PID: The Process ID of the child process.
      Parent ID: The Parent Process ID (should be the PID of the parent process).
      Command: The command line used to start the child process.
      Executable Path: The path to the executable file of the child process.
      User: The username of the child process owner.
      CPU Times: The amount of time the child process has spent in user and system mode.
      Memory Info: Resident Set Size (RSS) and Virtual Memory Size (VMS) of the child process.
      Start Time: The time when the child process started.
      Current Working Directory: The current working directory of the child process.
  
  Process Search
  
      By PID: Allows searching for a process using its Process ID.
      By Name: Allows searching for processes by their name.
  
  User Interface
  
      Color Coding: Uses color coding to distinguish different types of information (e.g., process details, file details, network details).
      Hierarchical Display: Indents child processes under their parent process, creating a tree-like structure.

SAMPLE OUTPUT:
```php
[●] Process Name: konsole  PID: 93256
 ├─ Parent ID: 58841
 ├─ Command: /usr/bin/konsole --workdir /home/dedsec/Desktop/
 ├─ Executable: /usr/bin/konsole
 ├─ User: dedsec
 ├─ CPU Times: User Time: 5.67, System Time: 0.77
 ├─ Memory Info: RSS: 162873344, VMS: 1486295040
 ├─ Start Time: Wed Jul 31 00:26:07 2024
 └─ Current Working Directory: /home/dedsec/Desktop/
   [●] Open Files:
    ├─ File Path: /home/dedsec/.local/share/mime/mime.cache
    │  ├─ File Descriptor (System Reference Number): 23
    │  ├─ File Type: application/octet-stream
    │  ├─ File Size: 123456 bytes
    │  ├─ Creation Time: Wed Jul 31 00:26:07 2024
    │  ├─ Modification Time: Wed Jul 31 00:26:07 2024
    │  └─ Access Time: Wed Jul 31 00:26:07 2024
    ├─ File Path: /var/lib/flatpak/exports/share/mime/mime.cache
    │  ├─ File Descriptor (System Reference Number): 24
    │  ├─ File Type: application/octet-stream
    │  ├─ File Size: 123456 bytes
    │  ├─ Creation Time: Wed Jul 31 00:26:07 2024
    │  ├─ Modification Time: Wed Jul 31 00:26:07 2024
    │  └─ Access Time: Wed Jul 31 00:26:07 2024
   [●] Network Connections:
    └─ Local Address: 192.168.1.36 PORT: 39922 - Remote Address: 192.168.1.1 PORT: 23 - Status: SYN_SENT
   [●] Child Processes:
    └─ Process Name: zsh  PID: 93272
     ├─ Parent ID: 93256
     ├─ Command: /usr/bin/zsh
     ├─ Executable: /usr/bin/zsh
     ├─ User: dedsec
     ├─ CPU Times: User Time: 0.13, System Time: 0.09
     ├─ Memory Info: RSS: 8085504, VMS: 9871360
     ├─ Start Time: Wed Jul 31 00:26:07 2024
     └─ Current Working Directory: /home/dedsec/Desktop/
       [●] Open Files:
        ├─ File Path: /usr/share/zsh/functions/Completion.zwc
        │  ├─ File Descriptor (System Reference Number): 13
        │  ├─ File Type: application/octet-stream
        │  ├─ File Size: 123456 bytes
        │  ├─ Creation Time: Wed Jul 31 00:26:07 2024
        │  ├─ Modification Time: Wed Jul 31 00:26:07 2024
        │  └─ Access Time: Wed Jul 31 00:26:07 2024
       [●] Network Connections:
        └─ No Network Connection found
       [●] Child Processes:
        └─ Process Name: code1.py  PID: 94076
         ├─ Parent ID: 93272
         ├─ Command: /bin/python3 ./code1.py
         ├─ Executable: /usr/bin/python3.11
         ├─ User: dedsec
         ├─ CPU Times: User Time: 0.05, System Time: 0.07
         ├─ Memory Info: RSS: 14934016, VMS: 19804160
         ├─ Start Time: Wed Jul 31 00:37:02 2024
         └─ Current Working Directory: /home/dedsec/Desktop/
           [●] Open Files:
            └─ No open files found
           [●] Network Connections:
            └─ Local Address: 192.168.1.36 PORT: 31726 - Remote Address: 34.207.243.93 PORT: 443 - Status: ESTABLISHED
            └─ Local Address: 192.168.1.36 PORT: 43546 - Remote Address: 140.12.113.25 PORT: 443 - Status: ESTABLISHED
            └─ Local Address: 192.168.1.36 PORT: 43298 - Remote Address: 34.127.148.161 PORT: 443 - Status: ESTABLISHED
            └─ Local Address: 192.168.1.36 PORT: 33156 - Remote Address: 34.117.223.93 PORT: 443 - Status: ESTABLISHED
```

## INSTALLATION 
    * git clone https://github.com/0xbitx/DEDSEC_PROC-HACKER.git
    * cd DEDSEC_PROC-HACKER
    * chmod +x dedsec_proc-hacker
    * sudo ./dedsec_proc-hacker

### TESTED ON FOLLOWING
* Kali Linux 
* Parrot OS 
* Ubuntu

## Support

If you find my work helpful and want to support me, consider making a donation. Your contribution will help me continue working on open-source projects.

**Bitcoin Address: `36ALguYpTgFF3RztL4h2uFb3cRMzQALAcm`**

<h1 align="center"> DISCLAIMER </h1>

<h4 align="center">I'm not responsible for anything you do with this program, so please only use it for good and educational purposes. </h4>
