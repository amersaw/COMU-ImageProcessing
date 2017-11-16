

```python
from scipy import ndimage
from scipy import misc
import matplotlib.pyplot as plt
import math
```

![Png](http://cdn.virtualnerd.com/tutorials/Alg1_13_01_0001/assets/Alg1_13_01_0001_D_01_09.png)


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

center = [im_size[0]/2, im_size[1]/2]
print('Center Point    : ', center)
```

    f tipi          :  <class 'numpy.ndarray'>
    Image Dimension :  3
    Image Size      :  (768, 1024, 3)
    Center Point    :  [384.0, 512.0]



```python
for i in range (im_size[0]):
    for j in range(im_size[1]):
        if(findDistance([i,j],center)>300):
            f[i,j,:] = 0
plt.imshow(f)
plt.show()
```


![png](Images/img_1_1.png?raw=true)



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


![png](Images/img_1_2.png?raw=true)
