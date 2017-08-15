# keras-frcnn
Using Faster R-CNN to detect small objects in drone data.

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
  <img src="https://github.com/shuuchen/keras-frcnn/blob/master/data/113.png" height="216" width="396" />
</p>

## License
* Released under the MIT license. See LICENSE for details.
