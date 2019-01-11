# Review-Face-Detection-Tech
Review the state-of-art face detection algorithm. Resources comes from internet. 

## Common issue in face detection
### Terms: 
  - partial occlusion 部分遮挡
  - silhouettes 轮廓

There are some common issues in face detection
  - `1#` 类似人脸的图案检测为人脸  detection non-facial as human face
  - `2#` 无法识别角度较大的侧脸或者占满屏幕的特写脸 can not detect human face if partial face or a full screen face

[Retrieved from:](https://github.com/AlfnXd/video_clipper/wiki/How-to-use) mtcnn 检测的准确率相比 dlib 的 cnn face detection 会低一些，比如会将类似人脸的图案检测为人脸（需要调整参数），对角度较大的侧脸或者占满屏幕的特写脸也无法识别。

### dlib vs MTCNN (Multi-Task CNN)
One problem with the above approach seems to be that the `Dlib face detector misses some of the hard examples (partial occlusion, silhouettes, etc)`. This makes the training set too "easy" which causes the model to perform worse on other benchmarks. To solve this, other face landmark detectors has been tested. One face landmark detector that has proven to work very well in this setting is the Multi-task CNN. A Matlab/Caffe implementation can be found [here Caffe-Face Project from QiaoYu](https://github.com/kpzhang93/) and this has been used for face alignment with very good results. A Python/Tensorflow implementation of MTCNN can be found in the FaceNet project. This implementation does not give identical results to the Matlab/Caffe implementation but the performance is very similar. (cited from FaceNet project https://github.com/davidsandberg/facenet)


## Experiment or demo
There are some source codes or online platform to test the face detection algorithms.
### 1. opencv default haarcascade_frontface model 
Online URL: https://docs.opencv.org/3.4/df/d6c/tutorial_js_face_detection_camera.html
Result: Failed badly on `1# and 2#`


## Tutorial of FaceDetection
### dlib in Python
Dlib tutorial (Python): https://blog.csdn.net/sunmc1204953974/article/details/49976045

这篇博客所述的人脸标记的算法也是来自Dlib库，Dlib实现了One Millisecond Face Alignment with an Ensemble of Regression Trees中的算法（http://www.csc.kth.se/~vahidk/papers/KazemiCVPR14.pdf 作者为Vahid Kazemi 和Josephine Sullivan）

Dlib (C++ or Python)实现了这篇最新论文的算法，所以Dlib的人脸标记算法是十分先进的，而且Dlib自带的人脸检测库也很准确，我们项目受到硬件所限，摄像头拍摄到的`画面比较模糊`，而在这种情况下之前尝试了几个人脸库，识别率都非常的低，而Dlib的效果简直出乎意料。

### dlib with Asia Face Model
百万张人脸训练的模型和源码，现全部开源了！附下载 http://cstor.cn/textdetail_12508.html


