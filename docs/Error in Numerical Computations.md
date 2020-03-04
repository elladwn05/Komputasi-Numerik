# Error in Numerical Computations

**Pengertian**

​	Error atau galat merupakan perbedaan antara hasil penyelesaian suatu model matematik secara numerik dengan penyelesaian secara analitis. Kesalahan yang terjadi sangatlah penting karena kesalahan dalam pemakaian algoritma pendekatan akan menyebabkan nilai kesalahan yang besar, sehingga pendekatan metode numerik selalu membahas tingkat kesalahan dan tingkat kecepatan proses yang akan terjadi.

​	Masalah-masalah matematika yang sering kita selesaikan biasanya menggunakan metode analitik atau metode sejati yaitu suatu metode yang memberikan solusi yang sesungguhnya karena memiliki galat (*error*) yang bernilai nol, tetapi penyelesaian dengan menggunakan metode analitik hanya terbatas tidak selalu bisa diterapkan, maka solusinya masih dapat dicari yaitu dengan menggunakan metode numerik. Pada metode numerik solusinya merupakan hampiran (pendekatan) terhadap solusi sejati.

**Nilai galat (nilai kesalahan)**

​	Besarnya kesalahan atas suatu nilai taksiran dapat dinyatakan secara kuantitatif dan kualitatif. Besarnya kesalahan yang dinyatakan secara kuantitatif disebut Kesalahan Absolut. Besarnya kesalahan yang dinyatakan secara kualitatif disebut dengan Kesalahan Relatif. 

**Absolute error**

​	Kesalahan absolut suatu kuantitas adalah nilai absolut dari selisih antara nilai sebenarnya X dan nilai perkiraan x. Ini dilambangkan dengan :
$$
Ea = |X - x|
$$
**Relative error**

​	Relative error biasa disebut sebagai kesalahan relatif dari suatu kuantitas adalah rasio kesalahan absolutnya terhadap nilai sebenarnya. Ini dilambangkan dengan :
$$
Er = |Xt - Xa / Xt|
$$
**Penyebab terjadinya error**

​	Dibedakan menjadi 3, yaitu :

1. Round-off-errors
2. Truncation errors
3. Inherent errors

**Penjelasan**

1. Round-off-errors

   ​	Perhitungan dengan metode numerik hampir selalu menggunakan bilangan riil. Masalah timbul bila komputasi numerik dikerjakan oleh mesin (dalam hal ini komputer) karena semua bilangan riil tidak dapat disajikan secara tepat di dalam komputer, keterbatasan komputer dalam menyajikan bilangan riil menghasilkan galat yang disebut galat pembulatan.

2. Truncation errors

   ​	Galat pemotongan adalah galat yang ditimbulkan oleh pembatasan jumlah komputasi yang digunakan pada proses metode numerik. Banyak metode dalam metode numerik yang penurunan rumusnya menggunakan proses iterasi yang jumlahnya tak terhingga, sehingga untuk membatasi proses penghitungan, jumlah iterasi dibatasi sampai langkah ke n. Hasil penghitungan sampai langkah ke n akan menjadi hasil hampiran dan nilai penghitungan langkah n keatas akan menjadi galat pemotongan. dalam hal ini galat pemotongan kan menjadi sangat kecil sekali jika nilai n di perbesar. Konsekuensinya tentu saja jumlah proses penghitungannya akan semakin banyak.

3. Inherent errors

   ​	Galat bawaan adalah galat dalam nilai data yang terjadi akibat kekeliruan dalam menyalin data, salah membaca skala atau kesalahan karena kurangnya pengertian mengenai hukum-hukum fisik dari data yang diukur. Kesalahan ini sering terjadi karena faktor human error.

**Maclaurin**

> ​	Suatu fungsi *f(x)* yang memiliki *f'(x), f''(x), f'''(x)*, dan seterusnya yang kontinyu dalam interval *I* dengan ![](D:\SEMESTER 4\KOMPUTASI NUMERIK\latex.png) maka untuk *x* disekitar *a* yaitu *![](D:\SEMESTER 4\KOMPUTASI NUMERIK\latex (1).png)*, *f(x)* dapat diekspansi kedalam deret taylor

​	Algoritma dari maclaurin

![](D:\SEMESTER 4\KOMPUTASI NUMERIK\taylor.png) 

dengan algoritma itu kita dapat menyederhanakan sebagai berikut :

![](D:\SEMESTER 4\KOMPUTASI NUMERIK\pendek.png)

**Listing program**

```python
import math

error = 0.001

def f(x):
    f_turunan = 1
    current=i=0
    iteration = True
    while iteration:
        old= current
        current += (f_turunan*(x**i))/math.factorial(i)
        print('f ke-', i,'=',current, 'Ea=', current-old )
        if current-old < error:
            iteration = False

        else:
            f_turunan *=3
            i +=1

f(4)
```

output

```
f ke- 0 = 1.0 Ea= 1.0
f ke- 1 = 13.0 Ea= 12.0
f ke- 2 = 85.0 Ea= 72.0
f ke- 3 = 373.0 Ea= 288.0
f ke- 4 = 1237.0 Ea= 864.0
f ke- 5 = 3310.6 Ea= 2073.6
f ke- 6 = 7457.799999999999 Ea= 4147.199999999999
f ke- 7 = 14567.285714285714 Ea= 7109.4857142857145
f ke- 8 = 25231.514285714286 Ea= 10664.228571428572
f ke- 9 = 39450.485714285714 Ea= 14218.971428571429
f ke- 10 = 56513.25142857143 Ea= 17062.765714285713
f ke- 11 = 75127.17766233766 Ea= 18613.926233766237
f ke- 12 = 93741.1038961039 Ea= 18613.926233766237
f ke- 13 = 110923.18965034965 Ea= 17182.085754245752
f ke- 14 = 125650.69172541745 Ea= 14727.502075067794
f ke- 15 = 137432.69338547168 Ea= 11782.00166005423
f ke- 16 = 146269.19463051236 Ea= 8836.50124504068
f ke- 17 = 152506.7249211293 Ea= 6237.530290616938
f ke- 18 = 156665.07844820726 Ea= 4158.3535270779685
f ke- 19 = 159291.4069916249 Ea= 2626.3285434176505
f ke- 20 = 160867.20411767552 Ea= 1575.797126050602
f ke- 21 = 161767.65961827585 Ea= 900.4555006003357
f ke- 22 = 162258.81716405787 Ea= 491.1575457820145
f ke- 23 = 162515.07327490064 Ea= 256.25611084277625
f ke- 24 = 162643.20133032204 Ea= 128.12805542140268
f ke- 25 = 162704.7027969243 Ea= 61.501466602261644
f ke- 26 = 162733.08808920227 Ea= 28.385292277962435
f ke- 27 = 162745.70377465914 Ea= 12.61568545686896
f ke- 28 = 162751.1104969978 Ea= 5.406722338666441
f ke- 29 = 162753.3477614138 Ea= 2.237264416005928
f ke- 30 = 162754.2426671802 Ea= 0.8949057663849089
f ke- 31 = 162754.58908231556 Ea= 0.34641513536917046
f ke- 32 = 162754.71898799133 Ea= 0.12990567577071488
f ke- 33 = 162754.7662264189 Ea= 0.04723842756357044
f ke- 34 = 162754.7828988051 Ea= 0.016672386205755174
f ke- 35 = 162754.7886150518 Ea= 0.005716246698284522
f ke- 36 = 162754.79052046736 Ea= 0.0019054155563935637
f ke- 37 = 162754.79113843996 Ea= 0.0006179726042319089
```

