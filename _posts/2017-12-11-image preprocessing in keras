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

```python
        x = x[..., -1]  # assume it is 3 channel image,  change RGB->BGR
        # Zero-center by mean pixel
        x[0, :, :] -= 103.939
        x[1, :, :] -= 116.779
        x[2, :, :] -= 123.68
        return x
```
