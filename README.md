## Table of Contents
* [How to Get Last Few Lines from a CSV File Using Windows PowerShell](#how-to-get-last-few-lines-from-a-csv-file-using-windows-powershell)
* [Useful Links](#useful-links)


### How to Get Last Few Lines from a CSV File Using Windows PowerShell
I had to see last few rows of a large CSV file (>16 GB); it was too large to open in Excel. So I obtained the last few rows from that file and wrote it to another file using Windows PowerShell. Input.csv is my large file and Output.csv is the output file.
- Use of get-content (or type) is obtained from this [link](https://www.csvexplorer.com/blog/open-big-csv/).
- Use of ASCII encoding is obtained from this [link](https://stackoverflow.com/questions/5596982/using-powershell-to-write-a-file-in-utf-8-without-the-bom) the third answer, by Lenny.
- Use of Append is obtained from this [link](https://powershell.org/2013/10/why-get-content-aint-yer-friend/).
```powershell
type -First 1 Input.csv | out-file "Output.csv" -encoding ASCII                # Getting heading
type -last 1000 Input.csv | out-file "Output.csv" -encoding ASCII -Append      # Getting last 1000 rows
```

### Useful Links
[Basics of writing Markdown files by Microsoft](https://docs.microsoft.com/en-us/azure/devops/project/wiki/markdown-guidance?view=azure-devops#:~:text=Paragraphs%20and%20line%20breaks,-Supported%20in%3A%20Definition&text=In%20a%20Markdown%20file%20or,text%20on%20a%20new%20line.)
