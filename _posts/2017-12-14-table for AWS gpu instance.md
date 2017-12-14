A basic table for some cheap AWS gpu instance <br>
There are some cheap GPU instance on AWS. Usually the basic type of that series of instance.<br>



| Instance | GPU type |	Computing Capability | GPUs	| GPU Memory	| vCPUs	| Main Memory	| Storage | Storage Statistics | spot price |
| ------------- | ------------- |	------------- | -------------	|------------- |-------------	| -------------	| ------------- | -------------| ------------- |
|g2.2xlarge instance |	GRID  K520| 3.0| ? |8GB| 8|15GB | SSD	 | 61GB SSD storage |~0.27$/h|
|p2.2xlarge instance |Tesla K80|3.7| 1 | 12GB |4| 61GB| EBS | High | ~0.3$/h|
|g3.4xlarge | Tesla M60| 5.2 |	1 | 8GB| 16	| **122GB**| EBS |3.5 Gbps | ~0.4$/h|
|p3.2xlarge instance | Tesla V100|7.0| 1| 16GB | 8 | 61 GB | EBS |1.5Gbps | ~1-1.5$/h|


Computing Capability refer to https://developer.nvidia.com/cuda-gpus<br>

 
**My experience** <br>
you can start to use G2, since it is the cheapest. You can finish your configuration of your environment. Once you get it done, you can create your AMI, and move to some better intance to train your model.  Since difference intance has **difference GPU computing capability**, you might need to **rebuild your files**(for caffe or yolo). make clean; make -j16; make pycaffe.  Otherwise, caffe or yolo might give you some weird errors.c <br>
if you hope to use larger GPU Memory, and increase your batch size, P2 is good, cheaper, and larger GPU memory. <br>
if you dont have that many images, and hope to get better computing speed, then use G3. <br>
usually, when the new instance come out, it will be cheaper in spot intances pricing. But will increase a lot <br><br>


**Unexpected break when using some instances in west zone - Oregon**<br> 
Oregon west zone might be the most latest zone, most latest instance seems to be firstly deployed in this zone, and then AWS will apply to some other zone.<br> 
But so many users are also in this zone, so the price is usually a little more expensive than other zone.<br>
But the most important bad part is, sometimes, when I bid some instance, it will stop for no reason. In the beginning, I thought it might because of my maximum price is too low. Say P2 instance, now is 0.27$/hour, but sometimes it increases to 1.2$/h. If I set my maximum acceptable is 0.8$/h, then my machine will stop suddenly. But later on, even I set the price to be 2$/h, and I have make sure that the maximum before my machine stop is much lower than that.  Still, it will stop for no reason.  <br>
Hence, I switch to east region, it does provide more stable service(May be just because less user use it in this region. <br>
When you immigrate to a new region(Ohio), if you still want to use your previous ami in the the previous region(Oregon for example), you might need to copy it to your new zone.
 
