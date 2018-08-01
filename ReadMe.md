This is caffe implementation of shuffleNet V2, For details, you can read the original paper:

"[ShuffleNet V2: Practical Guidelines for Efficient CNN Architecture Design](https://arxiv.org/abs/1807.11164)"

This model's shuffle_channel cuda file for acceleration is based on [farmingyard/ShuffleNet.](https://github.com/farmingyard/ShuffleNet)  conv_dw_layer cuda file is based on [farmingyard/caffe-mobilenet](https://github.com/farmingyard/caffe-mobilenet)

Note: If you want to train Shufflenet V2 on caffe, firstly, you should add all of *.cu and *.cpp to src/caffe/layers, and add all of *.hpp to include/caffe/layers . Then， you need change the `caffe.proto` :



    message LayerParameter {
    ...
    optional ShuffleChannelParameter shuffle_channel_param = 164;
    ...
    }
    ...
    message ShuffleChannelParameter {
      optional uint32 group = 1[default = 1]; // The number of group
    }

If you have no clue about how to add the ShuffleChannel layer and ConvolutionDepthwise layer, take this blog"ShuffleNet在Caffe框架下的实现" as a reference.
