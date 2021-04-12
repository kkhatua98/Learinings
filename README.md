## How to Get Last Few Lines from a CSV File Using Windows PowerShell
I had to work with some CSV file of size greater than 16 GB, so it was not opening completely with Excel, as a result I could not see the rows towards the last of the file. So I did this. ABCD.csv is my large file; from this file we are obtaining last 1000 rows and writing it to some other file.
Use of get-content (or type) is obtained from this [link](https://www.csvexplorer.com/blog/open-big-csv/).
Use of ASCII encoding is obtained from this [link](https://stackoverflow.com/questions/5596982/using-powershell-to-write-a-file-in-utf-8-without-the-bom) the third answer, by Lenny.
Use of Append is obtained from this [link](https://powershell.org/2013/10/why-get-content-aint-yer-friend/).
```
type -First 1 ABCD.csv | out-file "Out_ABCD.csv" -encoding ASCII                # Getting heading
type -last 1000 ABCD.csv | out-file "Out_ABCD.csv" -encoding ASCII -Append      # Getting last 1000 rows
```
