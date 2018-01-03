
# **Ödev**: Rastgele üretilen bir matrisin frekans değerleri


```python
from scipy.ndimage import imread
from scipy.misc import imsave
import matplotlib.pyplot as plt
import numpy as np
```


```python
img = np.random.randint(0,256,(4000))
res = np.zeros(256)
for i in img:
    res[i] += 1

interval = 16
for i in range(0, 256, interval):
    toplam = sum(res[i:i + interval])
    start = i
    end = i + interval -1
    print('{}\t-\t{}\t : {}'.format(start, end, toplam))

print('Toplam pixel sayisi : ', sum(res))
print('Ortalama renk bulunma sayisi: ', res.mean())
```

    0	-	15	 : 262.0
    16	-	31	 : 245.0
    32	-	47	 : 289.0
    48	-	63	 : 244.0
    64	-	79	 : 242.0
    80	-	95	 : 248.0
    96	-	111	 : 250.0
    112	-	127	 : 254.0
    128	-	143	 : 255.0
    144	-	159	 : 231.0
    160	-	175	 : 249.0
    176	-	191	 : 244.0
    192	-	207	 : 274.0
    208	-	223	 : 227.0
    224	-	239	 : 239.0
    240	-	255	 : 247.0
    Toplam pixel sayisi :  4000.0
    Ortalama renk bulunma sayisi:  15.625


Yükarıdaki görüldüğü gibi, tüm değerler birbirine yakın, demek ki randomization dengeli bir şekilde üretildi
