```python
from bs4 import BeautifulSoup
import requests
import smtplib
import time
import datetime

```


```python
URL='https://www.amazon.in/All-new-Echo-Dot-3rd-Gen/dp/B07PDHTHNN/ref=zg-bs_amazon-renewed_sccl_1/257-7269099-3717247?pd_rd_w=kakgN&content-id=amzn1.sym.7dd29d48-66c1-486c-967d-2ed40101f2ea&pf_rd_p=7dd29d48-66c1-486c-967d-2ed40101f2ea&pf_rd_r=WZY5W77AD4GF63DKE14Q&pd_rd_wg=RHobG&pd_rd_r=2b38c0d9-8126-4093-8374-f98b5352ecc7&pd_rd_i=B07PDHTHNN&psc=1'

headers={"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.108 Safari/537.36", "Accept-Encoding":"gzip, deflate", "Accept":"text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8", "DNT":"1","Connection":"close", "Upgrade-Insecure-Requests":"1"}

page = requests.get(URL, headers=headers)
soup1 = BeautifulSoup(page.content, "html.parser")

soup2 = BeautifulSoup(soup1.prettify(), "html.parser")

title = soup2.find(id='productTitle').text.strip()
price= soup2.find('span',{'class':"a-price-whole"}).text.strip()



print(title)
print(price)

```

    Echo Dot (3rd Gen), Certified Refurbished, Black – Improved smart speaker with Alexa – Like new, backed with 1-year warranty
    2,999
                              
                               .
    


```python
import datetime

today = datetime.date.today()

print(today)


```

    2023-05-09
    


```python
import csv
header=['Title', 'price']
data=[title, price]

with open('amazon.csv','w', newline='',encoding='UTF8') as csv_file:
    writer=csv.writer(csv_file)
    writer.writerow(header)
    writer.writerow(data)
```


```python



```


    ---------------------------------------------------------------------------

    FileNotFoundError                         Traceback (most recent call last)

    ~\AppData\Local\Temp\ipykernel_11688\3515916710.py in <module>
          1 import pandas as pd
    ----> 2 df = pd.read_csv(r'F:\AmazonWebScraperDataset.csv')
          3 print(df)
    

    ~\anaconda3\lib\site-packages\pandas\util\_decorators.py in wrapper(*args, **kwargs)
        309                     stacklevel=stacklevel,
        310                 )
    --> 311             return func(*args, **kwargs)
        312 
        313         return wrapper
    

    ~\anaconda3\lib\site-packages\pandas\io\parsers\readers.py in read_csv(filepath_or_buffer, sep, delimiter, header, names, index_col, usecols, squeeze, prefix, mangle_dupe_cols, dtype, engine, converters, true_values, false_values, skipinitialspace, skiprows, skipfooter, nrows, na_values, keep_default_na, na_filter, verbose, skip_blank_lines, parse_dates, infer_datetime_format, keep_date_col, date_parser, dayfirst, cache_dates, iterator, chunksize, compression, thousands, decimal, lineterminator, quotechar, quoting, doublequote, escapechar, comment, encoding, encoding_errors, dialect, error_bad_lines, warn_bad_lines, on_bad_lines, delim_whitespace, low_memory, memory_map, float_precision, storage_options)
        676     kwds.update(kwds_defaults)
        677 
    --> 678     return _read(filepath_or_buffer, kwds)
        679 
        680 
    

    ~\anaconda3\lib\site-packages\pandas\io\parsers\readers.py in _read(filepath_or_buffer, kwds)
        573 
        574     # Create the parser.
    --> 575     parser = TextFileReader(filepath_or_buffer, **kwds)
        576 
        577     if chunksize or iterator:
    

    ~\anaconda3\lib\site-packages\pandas\io\parsers\readers.py in __init__(self, f, engine, **kwds)
        930 
        931         self.handles: IOHandles | None = None
    --> 932         self._engine = self._make_engine(f, self.engine)
        933 
        934     def close(self):
    

    ~\anaconda3\lib\site-packages\pandas\io\parsers\readers.py in _make_engine(self, f, engine)
       1214             # "Union[str, PathLike[str], ReadCsvBuffer[bytes], ReadCsvBuffer[str]]"
       1215             # , "str", "bool", "Any", "Any", "Any", "Any", "Any"
    -> 1216             self.handles = get_handle(  # type: ignore[call-overload]
       1217                 f,
       1218                 mode,
    

    ~\anaconda3\lib\site-packages\pandas\io\common.py in get_handle(path_or_buf, mode, encoding, compression, memory_map, is_text, errors, storage_options)
        784         if ioargs.encoding and "b" not in ioargs.mode:
        785             # Encoding
    --> 786             handle = open(
        787                 handle,
        788                 ioargs.mode,
    

    FileNotFoundError: [Errno 2] No such file or directory: 'F:\\AmazonWebScraperDataset.csv'



```python

```
