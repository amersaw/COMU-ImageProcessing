
# Obje Sayisi Bulma


```python
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.pyplot import imread
from scipy.misc import imsave
import myutils
import math
```


```python
external_masks = np.array([  [[0,1],[1,1]], [[1,0],[1,1]], [[1,1],[0,1]], [[1,1],[1,0]]])
internal_masks = np.array([  [[1,0],[0,0]], [[0,1],[0,0]], [[0,0],[1,0]], [[0,0],[0,1]]])

def object_count(image,threshold=150):
    c_1=0
    c_2=0   
    m,n=image.shape
    for i in range(m-1):
        for j in range(n-1):
            for mask in internal_masks:
                if False not in (image[i:i+2,j:j+2]==mask):
                    c_1=c_1+1
            for mask in external_masks:
                if False not in (image[i:i+2,j:j+2]==mask):
                    c_2=c_2+1
    res=math.fabs((c_2-c_1)/4)
    return int(res)
```

## Çalıştırma örneği

`obj_count` klasöründe bulunan 3 tane fotoğraf üzerinde çalıştıralım :


```python
for i in range(1,4):
    image=myutils.convert_RGB_to_BW(imread('obj_count/objects{}.jpg'.format(i)))
    c = object_count(image)
    plt.subplot(1,3,i).set_title('Count: '+str(c))
    plt.imshow(image, cmap='gray')
plt.show()

```


![png](Images/img_14_1.png?raw=true)
