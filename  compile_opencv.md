### 编译opencv程序时候报错
```
g++   -L/usr/local/lib   -lopencv_core -lopencv_imgproc -lopencv_highgui -lopencv_ml -lopencv_imgcodecs -lopencv_features2d -lopencv_photo -lopencv_calib3d -lopencv_videostab -lopencv_video -lopencv_stitching -lopencv_superres -lopencv_flann -lopencv_shape -lopencv_videoio -lopencv_objdetect -o test1 test1.o  
test1.o: In function `main':
test1.cpp:(.text+0x33): undefined reference to `cv::Mat::zeros(int, int, int)'
test1.cpp:(.text+0x79): undefined reference to `cv::Mat::zeros(int, int, int)'
test1.cpp:(.text+0x2c1): undefined reference to `cv::imshow(cv::String const&, cv::_InputArray const&)'
test1.cpp:(.text+0x325): undefined reference to `cv::imshow(cv::String const&, cv::_InputArray const&)'
test1.cpp:(.text+0x34d): undefined reference to `cv::waitKey(int)'
test1.o: In function `cv::String::String(char const*)':
test1.cpp:(.text._ZN2cv6StringC2EPKc[_ZN2cv6StringC5EPKc]+0x4f): undefined reference to `cv::String::allocate(unsigned long)'
test1.o: In function `cv::String::~String()':
test1.cpp:(.text._ZN2cv6StringD2Ev[_ZN2cv6StringD5Ev]+0x14): undefined reference to `cv::String::deallocate()'
test1.o: In function `cv::String::operator=(cv::String const&)':
test1.cpp:(.text._ZN2cv6StringaSERKS0_[_ZN2cv6StringaSERKS0_]+0x28): undefined reference to `cv::String::deallocate()'
test1.o: In function `cv::Mat::~Mat()':
test1.cpp:(.text._ZN2cv3MatD2Ev[_ZN2cv3MatD5Ev]+0x39): undefined reference to `cv::fastFree(void*)'
test1.o: In function `cv::Mat::release()':
test1.cpp:(.text._ZN2cv3Mat7releaseEv[_ZN2cv3Mat7releaseEv]+0x4b): undefined reference to `cv::Mat::deallocate()'
collect2: error: ld returned 1 exit status
make: *** [test1] Error 1

```
#### 解决办法
修改makefile
```
INCLUDES = -I/usr/local/include/opencv                                                  
LIBS = -lopencv_core -lopencv_imgproc -lopencv_highgui -lopencv_ml -lopencv_imgcodecs  \
-lopencv_features2d  \
-lopencv_photo  \
-lopencv_calib3d\
-lopencv_videostab\
-lopencv_video\
-lopencv_stitching\
-lopencv_superres\
-lopencv_flann\
-lopencv_shape\
-lopencv_videoio\
-lopencv_objdetect

LIBDIRS = -L/usr/local/lib

CC=g++

OBJS= test1.o

test1:$(OBJS)
        $(CC) $^ -o $@ $(LIBDIRS) $(LIBS)

```
