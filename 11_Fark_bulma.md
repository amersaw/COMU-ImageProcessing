
# Fark Bulma
iki fotoğrafı birbirinden çıkartarak (çıkartma işlemi yaparak) herhangi bir fotoğrafa bir müdahele yapıldıysa gözükebilir.


```python
from matplotlib.pyplot import imread as imread
from scipy import misc
import matplotlib.pyplot as plt
import numpy as np
%matplotlib inline
def_fig_size = plt.rcParams["figure.figsize"]
plt.rcParams["figure.figsize"] = [12,9]

```

## Fotoğraflar yüklemek


```python
img_original = imread('diff_org.jpg')
img_modified = imread('diff_mod.jpg')
plt.subplot(1,2,1), plt.imshow(img_modified, shape=(400,600))
plt.subplot(1,2,2), plt.imshow(img_original, shape=(400,600))
plt.show()
```


![png](Images/img_11_1.png?raw=true)



```python
img_diff = img_original - img_modified
```

Elde edilen fotoğrafı görüntüleyelim :


```python
plt.rcParams["figure.figsize"] = def_fig_size
plt.imshow(img_diff)
plt.show()

```


![png](Images/img_11_2.png?raw=true)
