# jampy-exe
Jam.py Demo v5.4.112 package as EXE

To package Jam.py Application as EXE, we need to install X86 Python for X64 Windows, and use pip to install pyinstaller. 
Than navigate to Jam.py Application folder and run:

```
pyinstaller -c -F --onefile --noconfirm --add-data "demo.sqlite;." --add-data "admin.sqlite;." --add-data "locks;locks" --add-data "js;js" --add-data "css;css" --add-data "reports;reports" --add-data "jam;jam" --add-data "static;static" --add-data "index.html;." --add-data "server.py;."  server.py --name=jampy_win_64.exe
```

Why packaged as EXE?
------------------------------------

Because we can't pay enough for hosting, to demonstrate how fast Jam.py is with huge databases!

Demonstrate what?
------------------------------------

With "Data Pump" button added on Demo, one can create HUGE SQLite database and see the performance avoiding the Net!
Closing the executable on X button erases all. 

Tested DB size
------------------------------------

We tested DB File size in bytes :  4570799104
