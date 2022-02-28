# Tugas Kecil 2 IF2211 Strategi Algoritma

**Dibuat oleh:** <br>
Flavia Beatrix Leoni A. S. - 13520051

## Deskripsi Singkat
Merupakan program yang mengimplementasikan Convex Hull dan dapat digunakan untuk melakukan visualisasi tes Linear Separability Dataset dengan algoritma Divide and Conquer. Himpunan titik pada bidang planar disebut convex jika untuk sembarang dua titik pada bidang tersebut (misal p dan q), seluruh segmen garis yang berakhir di p dan q berada pada himpunan tersebut. Pustaka myConvexHull memiliki parameter berupa array yang berisi kumpulan koordinat titik yang ingin dicari Convex Hull-nya dan mengembalikan array simplicesnya, yaitu kumpulan pasangan indeks pada array masukan dari titik-titik yang membentuk garis pada Convex Hull.

## Requirement
- Python
- Library numpy, dapat di-install dengan menuliskan command berikut pada terminal
```
pip install numpy
```
- Library pandas, dapat di-install dengan menuliskan command berikut pada terminal
```
pip install pandas
```
- Library matplotlib, dapat di-install dengan menuliskan command berikut pada terminal
```
pip install matplotlib
```
- Library sklearn, dapat di-install dengan menuliskan command berikut pada terminal
```
pip install scikit-learn
```

## Cara Menggunakan
1. Pastikan semua requirement telah terinstall dengan baik
2. Buka file `myConvexHull.ipynb` yang terdapat dalam folder src
3. Jalankan cell yang berisi pustaka myConvexHull
4. Pustaka myConvexHull telah dapat digunakan pada kode program lain
5. Contoh penggunakan pustaka myConvexHull pada visualisasi tes linear separability dataset untuk dataset dari sklearn adalah sebagai berikut
```
data_iris = datasets.load_iris()
# create a DataFrame
df = pd.DataFrame(data_iris.data, columns=data_iris.feature_names)
df['Target'] = pd.DataFrame(data_iris.target)
# visualisasi hasil ConvexHull
plt.figure(figsize = (10, 6))
colors = ['b','r','g']
plt.title('Sepal Width vs Sepal Length')
plt.xlabel(data_iris.feature_names[0])
plt.ylabel(data_iris.feature_names[1])
for i in range(len(data_iris.target_names)):
  bucket = df[df['Target'] == i]
  bucket = bucket.iloc[:,[0,1]].values
  simplices = myConvexHull(bucket) # implementasi pustaka myConvexHull
  plt.scatter(bucket[:, 0], bucket[:, 1], label=data_iris.target_names[i])
  for simplex in simplices:
    plt.plot(bucket[simplex, 0], bucket[simplex, 1], colors[i])
plt.legend()
```