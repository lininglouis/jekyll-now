Suppose you read a image into 
```python
img_cv2.astype(np.float32).mean(axis=(0,1)) 
# array([ 50.05013657,  54.32004547,  63.17078018], dtype=float32)
c=img_cv2.astype(np.double).mean(axis=(0,1)) 
#array([ 66.6539235 ,  75.00896196,  88.92087688])
```

**channel mean**<br>
**default cv2 uint8 channel mean**
```
img_cv2.mean(axis=(0,1))
Out[195]: array([ 66.6539235 ,  75.00896196,  88.92087688])
```

**double type channel mean**
```
img_cv2.astype(np.double).mean(axis=(0,1)) 
Out[193]: array([ 66.6539235 ,  75.00896196,  88.92087688])
```

**float32 type channel mean**
```
img_cv2.astype(np.float32).mean(axis=(0,1)) 
Out[194]: array([ 50.05013657,  54.32004547,  63.17078018], dtype=float32)
```


**global mean**
```
img_cv2.mean()
76.861254112045145

img_cv2.astype(np.float32).mean() 
76.861031

img_cv2.astype(np.double).mean() 
76.861254112045145
```


**Summary**<br>
in a word, the uin8 statistics is the same as the np.double.   The np.float32 is somehow inconsistent with other two format. Not sure the reason.



