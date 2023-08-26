![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/5b993918-ad46-4ea7-b522-f31b9177a8ad)# Ex02-Outlier
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

CODE and OUTPUT:
```
import pandas as pd
import seaborn as sns
from scipy import stats
import numpy as np
```
```
from google.colab import files
uploaded = files.upload()
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/4906cc2b-678d-4185-ab0a-d089e16e75b9)
```
df = pd.read_csv("bhp.csv")
q1 = df['price_per_sqft'].quantile(0.25)
q2 = df['price_per_sqft'].quantile(0.5)
q3 = df['price_per_sqft'].quantile(0.75)
iqr = q3-q1
iqr
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/f30f6568-991d-4048-b244-3fbcdcb937ab)
```
low = q1-1.5*iqr
low
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/254e7703-ae3a-46e6-960a-9b37a21b3535)
```
high = q3+1.5*iqr
high
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/4ac387cd-b9e6-4785-8464-66869f6f6ef7)
```
df = df[((df['price_per_sqft']>=low) & (df['price_per_sqft']<=high))]
df
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/4152d83f-5aef-4c1a-8092-e76536ebd0ce)
```
z = np.abs(stats.zscore(df['price_per_sqft']))
z
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/a0da48ac-99fe-4e6c-9b8b-b39c5d8121a8)
```
df1 = df[z<3]
df1
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/3fef3a7c-8551-43c0-80d7-5a2188e00a5c)


```
from google.colab import files
uploaded = files.upload()
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/883c893f-2e8b-4b3f-b4dc-77307ed980a8)
```
df = pd.read_csv("height_weight.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/0eeee5cc-a508-4252-92df-59880e59de13)
```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/8b1eeea4-5908-4568-86be-c2127de0797f)
```
high = q3+1.5*iqr
high
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/26ab4343-bd7e-4331-b1dd-af96823456a3)
```
df = df[((df['height'] >=low) & (df['height']<= high))]
df
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/bcb2a88f-eba1-4b59-8d19-2e88130b13e1)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/d7160f8d-1321-46dc-9051-961dd9cb40eb)
```
df1 = df[z<3]
df1
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/afb8af88-3aa2-4d96-889d-26b9eba19149)
```
df = pd.read_csv("height_weight.csv")
q1 = df['weight'].quantile(0.25)
q2 = df['weight'].quantile(0.5)
q3 = df['weight'].quantile(0.75)
iqr = q3-q1
iqr
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/222beeb7-a893-4793-b96e-7e42294934d7)
```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/8b66b76e-f387-4e40-b594-ac6ca0a4284a)
```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/bbe28186-2247-4005-a89f-064c994354ad)
```
df1 = df[((df['weight'] >=low) & (df['weight']<= high))]
df1
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/7653872e-b6da-4b22-a613-24a5b54f464c)
```
z = np.abs(stats.zscore(df1['weight']))
z
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/de553057-bd66-4348-8cfe-0f4a305ca42b)
```
df2 = df1[z<3]
df2
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/ea3cd452-e6f1-424d-ae10-5e0304850dd5)

```
from google.colab import files
uploaded = files.upload()
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/2f364b31-ca6a-410a-940f-e152c6237c11)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/31e84543-2e24-4ac6-babf-3b897de05fef)
```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/efadafd3-56fd-4d33-93f1-f2faa1fbf207)
```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/42671517-822a-4e56-a9c2-ff36efcdf1a3)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/4533fa2e-bb09-4ced-8042-c89f05f01914)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/29d6abf2-8194-4cba-820d-016360331e79)
```
df1 = df[z<3]
df1
```
![image](https://github.com/Vaish-1011/ODD2023---Datascience---Ex-02/assets/135130074/ef493174-a3ca-44fc-89ad-1889d4670f47)


















