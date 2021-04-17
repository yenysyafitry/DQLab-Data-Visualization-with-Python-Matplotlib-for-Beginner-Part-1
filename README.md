###Pengenalan Dataset 
```plantuml
import pandas as pd
dataset = pd.read_csv('https://dqlab-dataset.s3-ap-southeast-1.amazonaws.com/retail_raw_reduced.csv')
print('Ukuran dataset: %d baris dan %d kolom\n' % dataset.shape)
print('Lima data teratas:')
print(dataset.head())
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/164/312/1447">Link materi : academy.dqlab.id/main/livecode/164/312/1447</a>

----

###Penambahan Kolom Order Month pada Dataset 
```plantuml
import datetime
dataset['order_month'] = dataset['order_date'].apply(lambda x: datetime.datetime.strptime(x, "%Y-%m-%d").strftime('%Y-%m'))
print(dataset.head())
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/164/312/1450">Link materi : academy.dqlab.id/main/livecode/164/312/1450</a>

----

###Penambahan Kolom GMV pada Dataset 
```plantuml
dataset['gmv'] = dataset['item_price'] * dataset['quantity']
print('Ukuran dataset: %d baris dan %d kolom\n' % dataset.shape)
print('Lima data teratas:')
print(dataset.head())
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/164/312/1451">Link materi : academy.dqlab.id/main/livecode/164/312/1451</a>

----

###Membuat Data Agregat 
```plantuml

monthly_amount = dataset.groupby('order_month')['gmv'].sum().reset_index()
print(monthly_amount)
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/164/313/1453">Link materi : academy.dqlab.id/main/livecode/164/313/1453</a>

----

###Plot Pertama: Membuat Line Chart Trend Pertumbuhan GMV 

```plantuml
import matplotlib.pyplot as plt
plt.plot(monthly_amount['order_month'], monthly_amount['gmv'])
plt.show()
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/164/313/1454">Link materi : academy.dqlab.id/main/livecode/164/313/1454</a>

----

###Cara Alternatif: Fungsi .plot() pada pandas Dataframe 
```plantuml
import matplotlib.pyplot as plt
dataset.groupby(['order_month'])['gmv'].sum().plot()
plt.show()
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/164/313/1455">Link materi : academy.dqlab.id/main/livecode/164/313/1455</a>

----

###Mengubah Figure Size 
```plantuml
import matplotlib.pyplot as plt
plt.figure(figsize=(15,5))
dataset.groupby(['order_month'])['gmv'].sum().plot()
plt.show()
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/164/314/1459">Link materi : academy.dqlab.id/main/livecode/164/314/1459</a>

----

###Menambahkan Title and Axis Labels 
```plantuml
import matplotlib.pyplot as plt
plt.figure(figsize=(15, 5))
dataset.groupby(['order_month'])['gmv'].sum().plot()
plt.title('Monthly GMV Year 2019')
plt.xlabel('Order Month')
plt.ylabel('Total GMV')
plt.show()
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/164/314/1461">Link materi : academy.dqlab.id/main/livecode/164/314/1461</a>

----

###Kustomisasi Title and Axis Labels 
```plantuml
import matplotlib.pyplot as plt
plt.figure(figsize=(15, 5))
dataset.groupby(['order_month'])['gmv'].sum().plot()
plt.title('Monthly GMV Year 2019', loc='center', pad=40, fontsize=20, color='blue')
plt.xlabel('Order Month', fontsize=15)
plt.ylabel('Total Amount', fontsize=15)
plt.show()
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/164/314/1462">Link materi : academy.dqlab.id/main/livecode/164/314/1462</a>

----

###Kustomisasi Line dan Point 
```plantuml
import matplotlib.pyplot as plt
plt.figure(figsize=(15, 5))
dataset.groupby(['order_month'])['gmv'].sum().plot(color='green', marker='o', linestyle='-.', linewidth=2)
plt.title('Monthly GMV Year 2019', loc='center', pad=40, fontsize=20, color='blue')
plt.xlabel('Order Month', fontsize=15)
plt.ylabel('Total Amount', fontsize=15)
plt.show()
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/164/314/1464">Link materi : academy.dqlab.id/main/livecode/164/314/1464</a>

----

###Kustomisasi Grid 
```plantuml
import matplotlib.pyplot as plt
plt.figure(figsize=(15, 5))
dataset.groupby(['order_month'])['gmv'].sum().plot(color='green', marker='o', linestyle='-.', linewidth=2)
plt.title('Monthly GMV Year 2019', loc='center', pad=40, fontsize=20, color='blue')
plt.xlabel('Order Month', fontsize=15)
plt.ylabel('Total Amount', fontsize=15)
plt.grid(color='darkgray', linestyle=':', linewidth=0.5)
plt.show()
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/164/314/2396">Link materi : academy.dqlab.id/main/livecode/164/314/2396</a>

----

###Kustomisasi Axis Ticks 
```plantuml
import matplotlib.pyplot as plt
plt.figure(figsize=(15, 5))
dataset.groupby(['order_month'])['gmv'].sum().plot(color='green', marker='o', linestyle='-.', linewidth=2)
plt.title('Monthly GMV Year 2019', loc='center', pad=40, fontsize=20, color='blue')
plt.xlabel('Order Month', fontsize=15)
plt.ylabel('Total Amount (in Billions)', fontsize=15)
plt.grid(color='darkgray', linestyle=':', linewidth=0.5)
labels, locations = plt.yticks()
plt.yticks(labels, (labels/1000000000).astype(int))
plt.show()
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/164/315/1467">Link materi : academy.dqlab.id/main/livecode/164/315/1467</a>

----

###Menentukan Batas Minimum dan Maksimum Axis Ticks 
```plantuml
import matplotlib.pyplot as plt
plt.figure(figsize=(15, 5))
dataset.groupby(['order_month'])['gmv'].sum().plot(color='green', marker='o', linestyle='-.', linewidth=2)
plt.title('Monthly GMV Year 2019', loc='center', pad=40, fontsize=20, color='blue')
plt.xlabel('Order Month', fontsize=15)
plt.ylabel('Total Amount (in Billions)', fontsize=15)
plt.grid(color='darkgray', linestyle=':', linewidth=0.5)
plt.ylim(ymin=0)
labels, locations = plt.yticks()
plt.yticks(labels, (labels/1000000000).astype(int))
plt.show()
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/164/315/1468">Link materi : academy.dqlab.id/main/livecode/164/315/1468</a>

----

###Menambahkan Informasi Pada Plot 
```plantuml
import matplotlib.pyplot as plt
fig = plt.figure(figsize=(15, 5))
dataset.groupby(['order_month'])['gmv'].sum().plot(color='green', marker='o', linestyle='-.', linewidth=2)
plt.title('Monthly GMV Year 2019', loc='center', pad=40, fontsize=20, color='blue')
plt.xlabel('Order Month', fontsize=15)
plt.ylabel('Total Amount (in Billions)', fontsize=15)
plt.grid(color='darkgray', linestyle=':', linewidth=0.5)
plt.ylim(ymin=0)
labels, locations = plt.yticks()
plt.yticks(labels, (labels/1000000000).astype(int))
plt.text(0.45, 0.72, 'The GMV increased significantly on October 2019', transform=fig.transFigure, color='red')
plt.show()
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/164/315/1470">Link materi : academy.dqlab.id/main/livecode/164/315/1470</a>

----

###Menyimpan Hasil Plot Menjadi File Image 
```plantuml
import matplotlib.pyplot as plt
fig = plt.figure(figsize=(15, 5))
dataset.groupby(['order_month'])['gmv'].sum().plot(color='green', marker='o', linestyle='-.', linewidth=2)
plt.title('Monthly GMV Year 2019', loc='center', pad=40, fontsize=20, color='blue')
plt.xlabel('Order Month', fontsize=15)
plt.ylabel('Total Amount (in Billions)', fontsize=15)
plt.grid(color='darkgray', linestyle=':', linewidth=0.5)
plt.ylim(ymin=0)
labels, locations = plt.yticks()
plt.yticks(labels, (labels/1000000000).astype(int))
plt.text(0.45,0.72, 'The GMV increased significantly on October 2019', transform=fig.transFigure, color='red')
plt.savefig('monthly_gmv.png')
plt.show()
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/164/315/1472">Link materi : academy.dqlab.id/main/livecode/164/315/1472</a>

----

###Pengaturan Parameter untuk Menyimpan Gambar 
```plantuml
import matplotlib.pyplot as plt
fig = plt.figure(figsize=(15, 5))
dataset.groupby(['order_month'])['gmv'].sum().plot(color='green', marker='o', linestyle='-.', linewidth=2)
plt.title('Monthly GMV Year 2019', loc='center', pad=40, fontsize=20, color='blue')
plt.xlabel('Order Month', fontsize=15)
plt.ylabel('Total Amount (in Billions)', fontsize=15)
plt.grid(color='darkgray', linestyle=':', linewidth=0.5)
plt.ylim(ymin=0)
labels, locations = plt.yticks()
plt.yticks(labels, (labels/1000000000).astype(int))
plt.text(0.45,0.72, 'The GMV increased significantly on October 2019', transform=fig.transFigure, color='red')
plt.savefig('monthly_gmv.png', quality=95)
plt.show()
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/164/315/1473">Link materi : academy.dqlab.id/main/livecode/164/315/1473</a>

----

###Studi Kasus dari Senja: Daily number of customers on Desember 
```plantuml
#Import library yang dibutuhkan
import datetime
import pandas as pd
import matplotlib.pyplot as plt
#Baca dataset retail_raw_reduced.csv
dataset = pd.read_csv('https://dqlab-dataset.s3-ap-southeast-1.amazonaws.com/retail_raw_reduced.csv')
#Buat kolom order_month
dataset['order_month'] = dataset['order_date'].apply(lambda x: datetime.datetime.strptime(x, "%Y-%m-%d").strftime('%Y-%m'))
#Buat kolom gmv
dataset['gmv'] = dataset['item_price'] * dataset['quantity']
#Plot grafik sesuai dengan instruksi
plt.figure(figsize=(10, 5))
dataset[dataset['order_month']=='2019-12'].groupby(['order_date'])['customer_id'].nunique().plot(color='red', marker='.', linewidth=2)
plt.title('Daily Number of Customers - December 2019', loc='left', pad=30, fontsize=20, color='orange')
plt.xlabel('Order Date', fontsize=15, color='blue')
plt.ylabel('Number of Customers', fontsize=15, color='blue')
plt.grid(color='darkgray', linestyle=':', linewidth=0.5)
plt.ylim(ymin=0)
plt.show()
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/164/316/1477">Link materi : academy.dqlab.id/main/livecode/164/316/1477</a>

----
