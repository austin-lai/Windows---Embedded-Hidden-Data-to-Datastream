# Windows Embedded Hidden Data to Datastream

> Austin Lai | August 8th, 2021

---

<!-- Description -->

Windows - Embedded Hidden Data to Datastream

<!-- /Description -->

<br />

## Table of Contents

<!-- TOC -->

- [Windows Embedded Hidden Data to Datastream](#windows-embedded-hidden-data-to-datastream)
    - [Table of Contents](#table-of-contents)
    - [Example 1](#example-1)
    - [Example 2 - DLL](#example-2---dll)

<!-- /TOC -->

## Example 1

1) Create normal text file called "normal.txt" with the word "testing"

      ` echo testing > normal.txt `

2) You can view the text file with notepad seemingly normal and with command below to show datastream of it

      ` dir /r normal.txt `

3) Add first hidden text file to the "normal.txt" datastream

      ` echo hidden_msg1 > normal.txt:hidden1.txt `

4) Add second hidden text file to the "normal.txt" datastream

      ` echo hidden_msg2 > normal.txt:hidden2.txt `

5) Add calc.exe to "normal.txt" datastream

      ` type C:\Windows\System32\calc.exe > normal.txt:calc.exe `

6) To view the first or sceond hidden text

      ```dos
      notepad normal.txt:hidden1.txt
      
      type normal.txt:hidden2.txt
      ```

7) To execute the calc.exe in the datastream of normal.txt

      ```dos
      forfiles /P C:\Windows\System32 /m notepad.exe /c "C:\Users\Austin.Lai\Desktop\normal.txt:calc.exe"

      wmic process call create "C:\Users\Austin.Lai\Desktop\normal.txt:calc.exe"
      ```

## Example 2 - DLL

```dos
type "C:\temp\messagebox64.dll" > "C:\Program Files (x86)\TeamViewer\TeamViewer13_Logfile.log:ADSDLL.dll"

rundll32 "C:\Program Files (x86)\TeamViewer\TeamViewer13_Logfile.log:ADSDLL.dll",DllMain
```

<br />

---

> Do let me know any command or step can be improve or you have any question you can contact me via THM message or write down comment below or via FB
