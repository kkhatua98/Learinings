## Table of Contents
1. [How to Get Last Few Lines from a CSV File Using Windows PowerShell](#how-to-get-last-few-lines-from-a-csv-file-using-windows-powershell)
2. [How to Create New Column Using Existing Two or More Columns in Pandas with apply Function](#how-to-create-new-column-using-existing-two-or-more-columns-in-pandas-with-apply-Function)
3. [How to Convert a Python File to Jupyter Notebook](#how-to-convert-a-python-file-to-jupyter-notebook)
4. [Useful Links](#useful-links)


### How to Get Last Few Lines from a CSV File Using Windows PowerShell
I had to see last few rows of a large CSV file (>16 GB); it was too large to open in Excel. So I obtained the last few rows from that file and wrote it to another file using Windows PowerShell. Input.csv is my large file and Output.csv is the output file.
- Use of get-content (or type) is obtained from this [link](https://www.csvexplorer.com/blog/open-big-csv/).
- Use of ASCII encoding is obtained from this [link](https://stackoverflow.com/questions/5596982/using-powershell-to-write-a-file-in-utf-8-without-the-bom) the third answer, by Lenny.
- Use of Append is obtained from this [link](https://powershell.org/2013/10/why-get-content-aint-yer-friend/).
```powershell
type -First 1 Input.csv | out-file "Output.csv" -encoding ASCII                # Getting heading
type -last 1000 Input.csv | out-file "Output.csv" -encoding ASCII -Append      # Getting last 1000 rows
```


### How to Create New Column Using Existing Two or More Columns in Pandas with apply Function
Suppose we have 3 columns in the data named A, B, C. Now, we want to create a column of tag, such that for each row its value will be A if value in collumn A is maxium, B if value in column B is maximum or value C if value in column C is maximum.
```python
# Function to derive tag
def tag_function(a, b, c):
    maximum_value = max(a, b, c)
    
    if maximum_value == a:
        tbr = "A"
    elif maximum_value == b:
        tbr = "B"
    elif maximum_value == c:
        tbr = "C"
    
    return tbr


data["tag"] = data[["A", "B", "C"]].apply(lambda x:tag_function(x["A"], x["B"], x["C"]), axis = 1)
```


### How to Convert a Python File to Jupyter Notebook
I have written this following this [link](https://pypi.org/project/ipynb-py-convert/). Suppose A.py is the file you want to convert to notebook.
- *Step 1 (Optional):* Put #%% (Do not put space after it, it will not work) before the chunk of code you want to put in a cell in notebook.
- *Step 2:* Install ipynb-py-convert. \
For base Python: 
    ```
    pip install ipynb-py-convert
    ```
    For Conda
    ```powershell
    conda install -c defaults -c conda-forge ipynb-py-convert
    ```
- *Step 3:* Write this command in the Command Prompt or Anaconda Prompt
    ````powershell
    ipynb-py-convert A.py A.ipynb
    ````

### Useful Links
- Basics of writing Markdown files by Microsoft. [Link](https://docs.microsoft.com/en-us/azure/devops/project/wiki/markdown-guidance?view=azure-devops#:~:text=Paragraphs%20and%20line%20breaks,-Supported%20in%3A%20Definition&text=In%20a%20Markdown%20file%20or,text%20on%20a%20new%20line.)


