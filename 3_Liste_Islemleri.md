
# Liste İşlemleri


```python
myList = [0, 1, 2]
```


```python
def createSiraliList(size):
    res = []
    for i in range(size):
        res.append(i)
    return res
```


```python
def listIncrement(liste, n):
    res = []
    for i in range(len(liste)):
        res.append(liste[i] + n)
    return res
```


```python
liste1 = createSiraliList(5)
print('liste1 = ', liste1)

liste2 = listIncrement(liste1, 7)
print('liste1\'e 7 arttiktan sonra liste2 = ', liste2)
```

    liste1 =  [0, 1, 2, 3, 4]
    liste1'e 7 arttiktan sonra liste2 =  [7, 8, 9, 10, 11]


## Numpy vs normal liste zamanlama


```python
%timeit normal_liste = listIncrement(createSiraliList(9000000), 1)
```

    1.54 s ± 39.6 ms per loop (mean ± std. dev. of 7 runs, 1 loop each)



```python
# Numpy kütüphanesi dahil ediyoruz
import numpy as np
%timeit np.arange(9000000)+1
np_list = np.arange(9000000)+1
```

    36.3 ms ± 1.97 ms per loop (mean ± std. dev. of 7 runs, 10 loops each)


Yükarıda görüldüğü gibi, 9 milyon elemanlı listeler için :
* Normal listenin oluşturma ve işletme süresi : ~1.54 saniye
* Numpy listenin oluşturma ve işletme süresi : ~0.036 saniye

### Aralıklar
Numpy ile tüm elemanları almak için bu syntax'ı kullanabiliriz 

(:) symbolu bu konuda tüm elemanları anlamına geliyor


```python
tmp = np_list[:]
```

Ama birden fazla sayı arasında yazılırsa şu anlamına geliyor:
+ Başlangıç : Bitiş
+ Başlangıç : Bitiş : Artırış


```python
# 0 indesli elemandan 499 elemana almaktadir
tmp = np_list[1:500] 
```

**Dikkat**: bitiş konumda verilen sayı dahil değildir, yani :
*    0  : 1   => 0 indesli sadece
*    0  : 0   => herhangi bir eleman
*    12 : 15 => 12, 13 ve 14 indesli elemanlar

