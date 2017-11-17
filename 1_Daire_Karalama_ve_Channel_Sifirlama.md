
## Uzaklık bulma (findDistance) fonksiyonu
Ellimizde 2 nokta var ise bu iki nokta arasındaki uzaklığı bulmak için aşağıdaki kuralı kullanabiliriz :

![Png](http://cdn.virtualnerd.com/tutorials/Alg1_13_01_0001/assets/Alg1_13_01_0001_D_01_09.png)

Hem **p** hem de **center** parametreyi list tipinden olacak, ve her birisi içinde sadece ve sadece 2 eleman vardır.
 1. elemanı, noktanın x koordinatörü
 2. elemanı, noktanın y koordinatörü

kabul ederek, uzaklığı buluyoruz


```python
from scipy import ndimage
from scipy import misc
import matplotlib.pyplot as plt
import math
```


```python
def findDistance(p, center):
    a = p[0] - center[0] # a = x2 - x1
    b = p[1] - center[1] # b = y2 - y1
    return math.sqrt(a*a + b*b) # return sqrt(a^2 + b^2)
```


```python
f = misc.face()
print('f tipi          : ', type(f))

im_size = f.shape
print('Image Dimension : ', f.ndim)
print('Image Size      : ', im_size)
```

    f tipi          :  <class 'numpy.ndarray'>
    Image Dimension :  3
    Image Size      :  (768, 1024, 3)


Center noktayı bulabilmek için :


```python
center = [im_size[0]/2, im_size[1]/2]
print('Center Point    : ', center)
```

    Center Point    :  [384.0, 512.0]


### Daire Karalama
Daire Karalama mantığı, fotoğraftaki ortak noktayı bulduktan sonra ve findDistance fonksiyonu kullanarak bu noktadan x uzakklıkta kalaın her nukta dışında siyah yapıyoruz.


```python
for i in range (im_size[0]):
    for j in range(im_size[1]):
        if(findDistance([i,j],center)>300):
            f[i,j,:] = 0
plt.imshow(f)
plt.show()
```


![png](Images/img_1_2.png?raw=true)



```python
no_red = misc.face()
no_green = misc.face()
no_blue = misc.face()

# RGB  = RED  GREEN  BLUE

# 0. kanalın(yani kırmıze RED) tüm değerleri 0 yapıyoruz
no_red[:,:,0] = 0

# 1. kanalın(yani yeşil GREEN) tüm değerleri 0 yapıyoruz
no_green[:,:,1] = 0

# 2. kanalın(yani mavi BLUE) tüm değerleri 0 yapıyoruz
no_blue[:,:,2] = 0

plt.subplot(1,4,1), plt.imshow(misc.face())
plt.subplot(1,4,2), plt.imshow(no_red)
plt.subplot(1,4,3), plt.imshow(no_green)
plt.subplot(1,4,4), plt.imshow(no_blue)

plt.show()
```


![png](Images/img_1_1.png?raw=true)
