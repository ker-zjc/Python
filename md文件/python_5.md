```python
import cv2
import numpy as np
```


```python
img = cv2.imread('E:/desktop/asd/table.jpg')
img2 = cv2.imread('E:/desktop/asd/mygirl with school.jpg')
```


```python
edge = cv2.Canny(cv2.cvtColor(img,cv2.COLOR_BGR2GRAY),100,150)
cv2.imwrite("edge.jpg",edge)
```




    True




```python
contours,h = cv2.findContours(edge,cv2.RETR_EXTERNAL,cv2.CHAIN_APPROX_SIMPLE)
```


```python
drawc = img.copy()
```


```python
drawc = cv2.drawContours(drawc,contours,-1,(255,0,0),2)
```


```python
cv2.imwrite("contour.jpg",drawc)
```




    True




```python
mask = np.zeros(img.shape,dtype = "uint8")
mask = cv2.drawContours(mask,contours,-1,(255,255,255),-1)
cv2.imwrite("mask.jpg",mask)
divide = cv2.bitwise_and(mask,img)
cv2.imwrite("divide.jpg",divide)
```




    True




```python
(x,y,w,h) = cv2.boundingRect(contours[-1])
```


```python
(x,y,w,h)
```




    (88, 43, 335, 298)




```python
cut_eat=divide[y:y + h,x:x + w]
cv2.imwrite("cuteat.jpg",cut_eat)
```




    True




```python
cut_mask=mask[y:y + h,x:x + w]
cv2.imwrite("cut_mask.jpg",cut_mask)
```




    True




```python
cut_not = cv2.bitwise_not(cut_mask)
cv2.imwrite("cut_not.jpg",cut_not)
```




    True




```python
cut_image2 = img2[50:50 + h, 50:50 + w]
cv2.imwrite("cut_image2.jpg",cut_image2)
```




    True




```python
cut_image2 = cv2.bitwise_and(cut_not,cut_image2)
cv2.imwrite("cut_image2.jpg",cut_image2)
```




    True




```python
cut_image2 = cv2.bitwise_or(cut_eat,cut_image2)
cv2.imwrite("cut_image2.jpg",cut_image2)
```




    True




```python
img2[50:50 + h, 50:50 + w] = cut_image2[:,:]
cv2.imwrite("merge.jpg",img2)#找了很久，换了很多张图，原来在左上角……
```




    True




```python

```


```python

```
