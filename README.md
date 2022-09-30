# jampy-exe
Jam.py Demo v5.4.112 package as EXE

To run this EXE
--------------------

Just download and double click on it. It is safe. Visit the Application by pointing the Web browser to localhost:8080

It is more or less the same Application as in here: https://jampyapp.pythonanywhere.com/

With added "Data pump" to specifically demonstrate the speed of Jam.py platform.

How to package any Jam.py Application
--------------------------------------

To package Jam.py Application as EXE, we need to install X86 Python for X64 Windows, and use pip to install pyinstaller. 
Than navigate to Jam.py Application folder, copy jam folder from Jam.py distribution in here and run:

```
pyinstaller -c -F --onefile --noconfirm --add-data "demo.sqlite;." --add-data "admin.sqlite;." --add-data "locks;locks" --add-data "js;js" --add-data "css;css" --add-data "reports;reports" --add-data "jam;jam" --add-data "static;static" --add-data "index.html;." --add-data "server.py;."  server.py --name=jampy_win_64.exe
```


To unpack this EXE
--------------------
Download https://github.com/extremecoders-re/pyinstxtractor
and:

```
python pyinstxtractor/pyinstxtractor.py jampy_win_64.exe
```

The content is from https://github.com/jam-py/jam-py, jam and demo folder.


Why packaged as EXE?
------------------------------------

Because we can't pay enough for hosting, to demonstrate how fast Jam.py is with huge databases!

Demonstrate what?
------------------------------------

With "Data Pump" button added on Demo, one can create HUGE SQLite database and see the performance avoiding the Net!
Closing the executable on X button erases all. 
It also clearly demonstrates the performance when using indexes. For example, all lookups should be indexed. Hence, 
when we do something like this:
```
UPDATE DEMO_TRACKS
SET TRACKS_SOLD = (SELECT SUM(QUANTITY) FROM DEMO_INVOICE_TABLE T WHERE T.TRACK = DEMO_TRACKS.ID AND T.DELETED = 0)
```
with huge dataset, the above update will take “forever” to finish. Not only that! Showing ALL Invoice details might be slow.
So how do we speed this up and demonstrate >1000x faster performance?

We can add one single index on `Application Builder/Details/InvoiceTable`, on the right hand side `Indices` button, `track` field.
Profit.

Application Builder?
--------------------
Yep. `localhost:8080/builder.html`

Tested DB size
------------------------------------

We tested DB File size in bytes :  4570799104

License
------------------------------------

MIT License.


