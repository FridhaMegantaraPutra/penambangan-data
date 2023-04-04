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

# UTS

### Import libraries

pertama yang harus di lakukan adalah mengimport library

```{code-cell}

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from matplotlib import rcParams
from matplotlib.cm import rainbow
%matplotlib inline
import warnings
warnings.filterwarnings('ignore')
import seaborn as sns



```

### Import dataset

import dataset

```{code-cell}
dataset = pd.read_csv('dataset.csv')
print(dataset)


```

selanjutnya yang di lakukan adalah untuk mengecek misssing value apabilah ada missing value akan di gunakan KNN untuk mencari data yang hilang tersebut

```{code-cell}
dataset.info()


```

total data ada 303 tanpa ada missing value

```{code-cell}
dataset.describe()

```

lalu cek ukuran datanya

```{code-cell}


dataset.shape


```

```{code-cell}
f,ax = plt.subplots(figsize=(25, 15))
sns.heatmap(dataset.corr(), annot=True, linewidths=0.5,linecolor="red", fmt= '.1f',ax=ax)
plt.show()


```

lalu kita pisahkan antara fiture dan label

```{code-cell}

X=dataset.iloc[:, 0:13]
X.head()



```

dan ini adalah labelnya yang telah di pisahkan

```{code-cell}

y=dataset.iloc[:,-1]
y.head()

```

lalu selanjutnya melakukan standarisasi data

$$z=\frac{x-\mu}{\sigma}$$

```{code-cell}
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
scaler.fit(X)
X = scaler.transform(X)
print(X)


```

membagi data menjadi data latih dan data uji

```{code-cell}
from sklearn.model_selection import train_test_split
bagi = X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
print(bagi)



```

```{code-cell}
from sklearn.naive_bayes import GaussianNB
from sklearn import metrics
classifier = GaussianNB()
classifier.fit(X_train, y_train)
y_pred = classifier.predict(X_test)
print(y_pred)



```

di atas adalah hasil prediksi dari data uji yang telah di latih
lalu yang harus kita lakukan adalah mengecek akurasinya

```{code-cell}

print('Accuracy Score:')
print(metrics.accuracy_score(y_test,y_pred))



```

```{tableofcontents}

```
