# MLDriveTF
TensorFlow based Object Detection for MLDrive (autonomous vehicle model)

## Overview

### Steps

1. Create label map file: https://github.com/NanoNets/RaspberryPi-ObjectDetection-TensorFlow/blob/master/python/create\_label\_map.py . This is basically just an indexed list of all possible labels written in correct protobuf format expected by tensorflow.
2. Create tf records from dataset: https://github.coCreate tf records from datasetm/NanoNets/RaspberryPi-ObjectDetection-TensorFlow/blob/master/python/create\_data\_tf\_record.py . This is where we:
    1. enumerate all labeled images from our dataset
    2. split it into train/test set (80% for training, 20% for test in our case)
    3. write it in correct format to respectively train.record and val.record files. See https://www.skcript.com/svr/why-every-tensorflow-developer-should-know-about-tfrecord/
3. Take the pipeline configuration from original model and update it with our values of:
    * label map path,
    * train TFRecord path,
    * test TFRecord path,
    * learning\_rate, batch\_size, train\_steps, eval\_steps, (optionally)
    * path to fine\_tune\_checkpoint (FIXME: what's that?). Initially, this should be a path to pre-trained checkpoint. Later this should be a path to latest checkpoint.
4. Start DetectionModel evaluation (FIXME: what's that?): https://github.com/tensorflow/models/blob/master/research/object\_detection/eval.py
5. Start the actual learning: https://github.com/tensorflow/models/blob/master/research/object\_detection/train.py

## References

* https://github.com/tensorflow/models
* https://github.com/tensorflow/models/tree/master/research/object\_detection
* https://medium.com/nanonets/how-to-easily-detect-objects-with-deep-learning-on-raspberrypi-225f29635c74
* https://github.com/NanoNets/RaspberryPi-ObjectDetection-TensorFlow
* https://github.com/NanoNets/TF-OD-Pi-Test
