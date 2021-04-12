## How to Get Last Few Lines from a CSV File Using Windows PowerShell
I had to see last few rows of a large CSV file (>16 GB); it was too large to open in Excel. So I obtained the last few rows from that file and wrote it to another file using Windows PowerShell. ABCD.csv is my large file and Out_ABCD.csv is the output file.
- Use of get-content (or type) is obtained from this [link](https://www.csvexplorer.com/blog/open-big-csv/).
- Use of ASCII encoding is obtained from this [link](https://stackoverflow.com/questions/5596982/using-powershell-to-write-a-file-in-utf-8-without-the-bom) the third answer, by Lenny.
- Use of Append is obtained from this [link](https://powershell.org/2013/10/why-get-content-aint-yer-friend/).
```powershell
type -First 1 Input.csv | out-file "Output.csv" -encoding ASCII                # Getting heading
type -last 1000 Input.csv | out-file "Output.csv" -encoding ASCII -Append      # Getting last 1000 rows
```
