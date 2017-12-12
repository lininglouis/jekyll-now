two types of preprocessing in  the preprocessing_input function of Keras

One types: "tf" mode, **zerp-cemter and normalize to  [-1,1]**<br>
```python
        img /= 127.5
        img -= 1.0
        return img
```

Another types: **only substract the mean**<br>
It will save the image data with the order of BGR channel.<br>
Keras use PIL read the image into numpy array with RGB channel order.

This is preocessing in ImageNet data, it substract the mean [103.939, 116.779, 123.68]  in BGR channel  
```python
        img = img[..., -1]  # assume it is 3 channel image,  change RGB->BGR
        # Zero-center by mean pixel in ImageNet
        img[0, :, :] -= 103.939  #B
        img[1, :, :] -= 116.779  #G
        img[2, :, :] -= 123.68   #R
        return x
```

If you have your own customized data, then <br>
        img_mean = img.mean(axis=(0,1))
        img[:, :, :] -= img_mean 
#        you may also do like this        
#        img[:, :, :] -= img_mean[0] #B
#        img[1, :, :] -= img_mean[1] #G
#        img[2, :, :] -= img_mean[2] #R



if you dont use preprocessing data, and hope to combine opencv and the same zero-center processing, just be aware of the BGR and RGB channel. If you make a mistake when using ImageNet data and the default [103.939, 116.779, 123.68] mean in BGR channel, you might get something wrong. 
```python
    img_path = ./xxx.jpg
    img_cv2_BGR = cv2.imread(img_path)
    
    img_PIL_RGB = np.array(Image.open(img_path))
    img_PIL_BGR = cv2.cvtColor(img_PIL_RGB, cv2.COLOR_RGB2BGR)
    
    # those two means in BGR channel should be the same
    assert(img_cv2_BGR.mean(axis=(0,1)),  img_PIL_BGR.mean(axis=(0, 1)))
    

The core function in Keras is the _preprocess_numpy_input function in imagenet.utils.py<br>
```python
def _preprocess_numpy_input(x, data_format, mode):
    if mode == 'tf':
        x /= 127.5
        x -= 1.
        return x

    if data_format == 'channels_first':
        if x.ndim == 3:
            # 'RGB'->'BGR'
            x = x[::-1, ...]
            # Zero-center by mean pixel
            x[0, :, :] -= 103.939
            x[1, :, :] -= 116.779
            x[2, :, :] -= 123.68
        else:
            x = x[:, ::-1, ...]
            x[:, 0, :, :] -= 103.939
            x[:, 1, :, :] -= 116.779
            x[:, 2, :, :] -= 123.68
    else:
        # 'RGB'->'BGR'
        x = x[..., ::-1]
        # Zero-center by mean pixel
        x[..., 0] -= 103.939
        x[..., 1] -= 116.779
        x[..., 2] -= 123.68
    return x


```




        
        
 
