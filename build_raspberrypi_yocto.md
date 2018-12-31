### raspberrypi平台用yocto 搭建自己的系统
#### get code
```
mkdir workdir
git clone git://git.yoctoproject.org/meta-raspberrypi
git clone git://git.yoctoproject.org/poky
git clone git://git.openembedded.org/meta-openembedded
```
#### build
```
source poky/oe-init-build-env rpi-build
cd rpi-build
vim conf/local.conf
添加MACHINE = "raspberrypi0"

vim conf/conf/bblayers.conf
构建最小系统 在bblayers.conf中添加
/media/rooth/ext4/workplace/raspberry-yocto/meta-raspberrypi \
/media/rooth/ext4/workplace/raspberry-yocto/meta-openembedded/meta-oe \
/media/rooth/ext4/workplace/raspberry-yocto/meta-openembedded/meta-multimedia \

bitbake rpi-basic-image



```
```
#### build SDK
```
bitbake rpi-basic-image -c populate_sdk
```

#### Add opencv lib

```
add conf/local.conf

CORE_IMAGE_EXTRA_INSTALL += "libopencv-core-dev libopencv-highgui-dev libopencv-imgproc-dev libopencv-objdetect-dev libopencv-ml-dev"
CORE_IMAGE_EXTRA_INSTALL += "opencv-apps opencv-dev python-modules"

