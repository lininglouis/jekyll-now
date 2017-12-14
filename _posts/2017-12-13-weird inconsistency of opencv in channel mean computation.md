Suppose you read a image into 
```python
img_cv2.astype(np.float32).mean(axis=(0,1)) 
# array([ 50.05013657,  54.32004547,  63.17078018], dtype=float32)
c=img_cv2.astype(np.double).mean(axis=(0,1)) 
#array([ 66.6539235 ,  75.00896196,  88.92087688])
```

#channel mean  <h1> tag
**default cv2 uint8 mean**
```
img_cv2.mean(axis=(0,1))
Out[195]: array([ 66.6539235 ,  75.00896196,  88.92087688])
```

**double format mean**
```
img_cv2.astype(np.double).mean(axis=(0,1)) 
Out[193]: array([ 66.6539235 ,  75.00896196,  88.92087688])
```

**float32 channel mean**
```
img_cv2.astype(np.float32).mean(axis=(0,1)) 
Out[194]: array([ 50.05013657,  54.32004547,  63.17078018], dtype=float32)
```

