
**function for calculation output shape**<br>
```
def getConv2DOutputShape(imageSideLength, kernel, padding,stride):
    return  (imageSide+2*padding-kernel)/stride + 1
    
def getMaxPoolOutputShape(imageSideLength, kernel,stride): #no padding for maxpool
    return  (imageSide-kernel)/stride + 1
```


**parmeters number for Conv2D**
by default image_channel is 3, (RGB channels) <br>
total parameter for one layer =  filters_num * (kernel_size * kernel_size * image_channel  + 1)  <br>
each filter need 1 bias parameter, so we add 1 for each filter
