---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.14.5
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
---

# 1.INI ADALAH TUGAS PERTAMAN SAYA MENGGUNAKAN HAMMING DISTANCE UNTUK MENGUKUR JARAK

```{code-cell}
import pandas as pd
import numpy as np
import seaborn as sb


```

```{code-cell}

winter = pd.read_csv("cuaca_baru2.csv")

print(winter)


```

```{code-cell}

winter['humidity'].replace(['high','normal'],
                        [1, 0], inplace=True)

winter['play'].replace(['yes', 'no'],
                        [1, 0], inplace=True)

winter['windy'].replace(['benar', 'salah'],
                        [1, 0], inplace=True)

print(winter)

```

```{code-cell}


binar = winter.loc[:,['humidity','windy','play']]
print(binar)





```

# ini adalah rumus hamming distance

$ d(x, y)=\frac{1}{n} \sum\_{n=1}^{n=n}\left|x_i-y_i\right| $

```{code-cell}



from scipy.spatial.distance import hamming
data = []
latihan = -1
id = -1
while latihan < 13:

    latihan = latihan + 1
    id      = id +1

    a =[winter.iloc[13,1],winter.iloc[13,2],winter.iloc[13,3]]
    b =[winter.iloc[latihan,1],winter.iloc[latihan,2],winter.iloc[latihan,3]]
    print('ke',id,'=>',a,b)


    hamming_distance = hamming(a,b)
    data.append(hamming_distance)

    print(hamming_distance)


```

```{code-cell}

urut = data.sort()
print(data)

```

```{code-cell}
no =-1
dat2=[]
for i in data:
  no=no+1
  masuk_data = urut,i

  dat2.append(masuk_data)

```

```{code-cell}

for i in dat2:
  print(i)

```

```{code-cell}

```

```{tableofcontents}

```
