# Brodmann17 Face Detector

You can use this forked repo to detect face in image/images/webcam and also for benchmarking face detection performance in AFW,PASCAL,FDDB,UFDD and WIDER face dataset. 

From Authors: We share here a version of Brodmann17's super fast and accurate face detection library.   
This detector is based on a proprietary deep-learning algorithm which allows to run highly accurate CNNs  
efficiently on **ARM** CPUs.

##### Disclaimer:
- This library is shared for non-commercial use only.  For advanced, more accurate version for commercial use please reach out at **partners@brodmann17.com**

| <img src="https://github.com/brodmann17/Brodmann17FaceDetector/blob/master/example/example_out.jpg" width="270" height="250"> | <img src="https://github.com/brodmann17/Brodmann17FaceDetector/blob/master/example/example2_out.jpg" width="270" height="250"> | <img src="https://github.com/brodmann17/Brodmann17FaceDetector/blob/master/example/example3_out.jpg" width="270" height="250"> |
--|--|--

#### Library Dependencies

- **OpenBLAS** 0.2.18 [Sourcecode](https://github.com/xianyi/OpenBLAS/releases/tag/v0.2.18)
 
- google **protobuf** 2.6.1 [Sourcecode](https://github.com/google/protobuf/releases/tag/v2.6.1)
 
    If you are using ubuntu 16.04 these libraries can installed by:
 
```
    sudo apt-get install libopenblas-dev libprotobuf-dev
```
  
#### Supported Architectures

 - Armv8a (aarch64) : linux, tested on Ubuntu 16.04
 - Armv7l (arm) : linux, tested on Fedora 22
 - Intel (x84_64) : linux, tested on Ubuntu 16.04
 
#### Speed Benchmark (1 x ARM cortex A72, Rockchip RK3399)
| Input Image Size | Process Time [ms] | FPS [1/s] |
| --- | --- | --- |
| 640x480 | 67.72 | 14.77 |
| 320x240 | 22.26 | 44.93 |


----
  
## Getting started (C++)
  
- Requirements:
 - CMake (at least 3.0.0) - can be installed by using:

```
        sudo apt-get install cmake
```
 - OpenCV (tested with 2.4.9.1) - can be installed by using:
```
        sudo apt-get install libopencv-dev
```

 - Run these commands

````
        cd example 
        mkdir build  
        cd build  
        cmake .. 
        make
        cd ..
````

#### 1. Test webcam
```
$./build/example -mode=0 -webcam=0
```
#### 2. Test single image
```
$./build/example -mode=1 -path=../image/1.jpg
```
#### 3. Test image lists
```
$./build/example -mode=2 -path=../image/
```
#### 4. Evaluation in benchmark dataset, detection files will be stored in `example/detections` folder. 
```
a) afw dataset
$./build/example -mode=3 -dataset=AFW -path=/path/to/afw/dataset/

b) PASCAL dataset
$./build/example -mode=3 -dataset=PASCAL -path=/path/to/pascal/dataset/

c) FDDB dataset
$./build/example -mode=3 -dataset=FDDB -path=/path/to/fddb/dataset/

d) WIDER_val dataset
#./build/example -mode=3 -dataset=WIDER_VAL -path=/path/to/wider/validation/dataset/

e) UFDD dataset
#./build/example -mode=3 -dataset=UFDD -path=/path/to/UFDD/validation/dataset/
```

## Getting started (python)
 - Requirements:
    - Python 2.x
    - Numpy
    - Matplotlib
    - OpenCV
```
        pip install numpy, matplotlib, opencv-python
```
    
 - Usage     
```python
        from brodmann17_face_detector import Detector
    
        im = cv2.imread("../example/example2.jpg")
        with Detector() as det:
            detections = det.detect(im)
```
    
  See python/example.ipynb for a full working example
