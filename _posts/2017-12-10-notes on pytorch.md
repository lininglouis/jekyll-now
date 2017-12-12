nn.module.MaxPool2d  nn.module.functional.MaxPool2d <br>
-----


pytorch use init to define needed static neural nets(excluding pooling). it defines pooling as a function like relu. <br>

pytorch variable to numpy <br>
You can retrieve a tensor held by the Variable, using the .data attribute. Then, this should work: var.data.numpy().
https://discuss.pytorch.org/t/how-to-transform-variable-into-numpy/104/2

pytorch data order<br>
batch_size, channel, h, w



torch.nn only supports mini-batches <br>
The entire torch.nn package only supports inputs that are a mini-batch of samples, and not a single sample.
For example, nn.Conv2d will take in a 4D Tensor of nSamples x nChannels x Height x Width.
If you have a single sample, just use input.unsqueeze(0) to add a fake batch dimension.
