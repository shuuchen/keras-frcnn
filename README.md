# keras-frcnn
Using Faster R-CNN to detect small objects in drone data.

## Papers and ideas
* The original paper is https://arxiv.org/abs/1506.01497
* The original paper ueses RPN proposals of the sizes 128, 256 and 512, which is too big for small objects. I modified the sizes to 16, 32 and 64. As the result shows, small objects can be detected with high accuracy. However, due to the high computational cost, the speed is not fast enough for real-time applications and can hardly be used in mobile applications. I 'd rather recommend SSD https://arxiv.org/pdf/1512.02325.pdf for real-time applications as it is an internally adaptive detecting algorithm which is fast and accurate. For mobile applications, you can modify the standard convs with depth-wise separable convs as in https://arxiv.org/pdf/1704.04861.pdf, which can decrease the number of training parameters significantly. The speed/accuracy trade-offs for different applications are summarized in https://arxiv.org/pdf/1611.10012.pdf.

## Requirements
* Keras 2
* Python 2
* Opencv 2+

## Pretrained models
* Resnet50 is used as the basic pre-trained model.

## Training on drone data
* Stanford drone dataset is used to train the model. http://cvgl.stanford.edu/projects/uav_data/
* The data should be transformed to VOC2012 format for using.

## How to train
* Simply specify the parameters
```python
python train_frcnn.py -p [input_data_path]  --num_epochs [num_epoch] --input_weight_path [basic_model_path]
```

## How to test
* Simply specify the test data path
```python
python test_frcnn.py -p [test_data_path]
```

## Results
<p>
  <img src="https://github.com/shuuchen/keras-frcnn/blob/master/data/113.png" height="432" width="792" />
</p>

## Thanks
* https://github.com/yhenon/keras-frcnn

## License
* Released under the MIT license. See LICENSE for details.
