A basic table for some cheap AWS gpu instance <br>
There are some cheap GPU instance on AWS. Usually the basic type of that series of instance.<br>



| Instance | GPU type |	Computing Capability | GPUs	| GPU Memory	| vCPUs	| Main Memory	| Storage | Storage Statistics | spot price |
| ------------- | ------------- |	------------- | -------------	|------------- |-------------	| -------------	| ------------- | -------------| ------------- |
|g2.2xlarge instance |	GRID  K520| 3.0| ? |8GB| 8|15GB | SSD	 | 61GB SSD storage |~0.27$/h|
|p2.2xlarge instance |Tesla K80|3.7| 1 | 12GB |4| 61GB| EBS | High | ~0.3$/h|
|g3.4xlarge | Tesla M60| 5.2 |	1 | 8GB| 16	| **122GB**| EBS |3.5 Gbps | ~0.4$/h|
|p3.2xlarge instance | Tesla V100|7.0| 1| 16GB | 8 | 61 GB | EBS |1.5Gbps | ~1-1.5$/h|


Computing Capability refer to https://developer.nvidia.com/cuda-gpus<br>

 
My experience <br>
you can start to use G2, since it is the cheapest. You can finish your configuration of your environment. Once you get it done, you can create your AMI, and move to some better intance to train your model.  Since difference intance has **difference GPU computing capability**, you might need to **rebuild your files**(for caffe or yolo). make clean; make -j16; make pycaffe.  Otherwise, caffe or yolo might give you some weird errors.c
if you hope to use larger GPU Memory, and increase your batch size, P2 is good, cheaper, and larger GPU memory.
if you dont have that many images, and hope to get better computing speed, then use G3.
