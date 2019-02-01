# keras-frcnn
Using Faster R-CNN to detect small objects in drone data.

## Papers and ideas
* The original paper is https://arxiv.org/abs/1506.01497
* The original paper ueses RPN proposals of the sizes 128, 256 and 512, which is too big for small objects. I modified the sizes to 16, 32 and 64. As the result shows, small objects can be detected with high accuracy. However, due to the high computational cost, the prediction speed is not fast enough for real-time applications and can hardly be used in mobile applications. I 'd rather recommend SSD https://arxiv.org/pdf/1512.02325.pdf for real-time applications as it is an internally adaptive detecting algorithm which is fast and accurate. For mobile applications, you can modify the standard convs with depth-wise separable convs as in https://arxiv.org/pdf/1704.04861.pdf, which decreases the number of training parameters significantly. The speed/accuracy trade-offs for different applications are summarized in https://arxiv.org/pdf/1611.10012.pdf.

## Requirements

* Pay attention to the versions of various libraries when using tensorflow on gpus. The following versions work well.
 * Keras 2.1.5
 * Python 3.5
 * tensorflow-gpu 1.4.0
 * CUDA 8.0
 * cudnn 6.0

## Pretrained models
* Resnet50 is used as the basic pre-trained model.

## Training on drone data
* Stanford drone dataset is used to train the model. http://cvgl.stanford.edu/projects/uav_data/
* The data must be transformed to VOC2012 format for using.

## How to train
* Simply specify the parameters
  * The input path should contain at least a VOC2012 directory.
  * Other parameters are specified in default, which are recommended to use.
```python
python train_frcnn.py -p [voc_data_path] --output_weight_path [**.hdf5] --num_epochs 20 
* There should be a voc2012 folder under [voc_data_path], where the training data is stored. 
```

## How to test
* Simply specify the test data path
```python
python test_frcnn.py -p [test_data_path]
```

## Prediction results
<p>
  <img src="https://github.com/shuuchen/keras-frcnn/blob/master/data/113.png" height="432" width="792" />
</p>

## Any questions
Please feel free to contact me if you have any questions. Wechat users can add me via dushuchen1022wind for direct communication.

## Thanks
* https://github.com/yhenon/keras-frcnn

## License
* Released under the MIT license. See LICENSE for details.
