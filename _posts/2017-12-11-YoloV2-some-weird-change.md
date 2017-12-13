# YoloV2-some-weird-change

I used the yolov2  since 2016,  I dont have problem with it. <br>
But when I retrain the data using YoloV2 latest in November, I cannot detect anything. <br>
I trained thousands of images in 40000 epochs. The average IOU is about 75%, but it did not detect anything in the 2017 November Yolo V2. I thought it might be not <br>
I went back to train only 20 images with 1000 epochs, and also get over 70% IOU, still it did not draw any bounding box in any even easy images.<br>

I finally got this done by using **AlexAB's branch(https://github.com/AlexeyAB/darknet)**. It has Linux and Windows environment(I tried both). All the model I trained using the 2017November yolov2 are able to predict bounding box in the AlexAB's branch.   I guess the YOLO author might change something in the end of last year, like cfg parsing or some other configuration stuff and cause this happen.


One thing need to mention(maybe not important):
In the **test_detector function of detector.c file** of 2016 yolov2, it uses parse_network_cfg(cfgfile)  to parse the cfg.
But in the same function of 2017 Nov yolov2, it changes to use parse_network_cfg_custom(cfgfile,1) to do the same thing.
But but, if you still use the old parse_network_cfg in the latest 2017 version, it will detect nothing, even all cfg and weights are right! I havent got time to look at the details, but the older function should be deprecated if the author does not use it. 
