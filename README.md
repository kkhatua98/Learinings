## How to Get Last Few Lines from a CSV File Using Windows PowerShell
I had to work with some CSV file of size greater than 16 GB, so it was not opening completely with Excel, as a result I could not see the rows towards the last of the file. So I did this.
Use of get-content (or type) is obtained from this [link]{https://www.csvexplorer.com/blog/open-big-csv/}.
Use of ASCII encoding is obtained from this [link]{https://stackoverflow.com/questions/5596982/using-powershell-to-write-a-file-in-utf-8-without-the-bom} The third answer, by Lenny.
Use of Append is obtained from this [link]{https://powershell.org/2013/10/why-get-content-aint-yer-friend/}.
>type -First 1 cov_20210302.csv | out-file "Small_COV_Last.csv" -encoding ASCII
>type -last 1000 cov_20210302.csv | out-file "Small_COV_Last.csv" -encoding ASCII -Append
