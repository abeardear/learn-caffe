> ubuntu环境下配置caffe开发环境，注意不是安装caffe，是在code::blocks中使用caffe  

####1. 头文件的搜索位置  
在Searchdirectories ->Compile中添加：  
`(CAFFE_ROOT)/include  
(CAFFE_ROOT)/build/src （caffe.pb.h 的位置）`
这里作者在caffe目录(CAFFE_ROOT)/include/caffe/proto里面找到的caffe.pb.h，所以也添加了  
`(CAFFE_ROOT)/include/caffe/proto`  

![头文件添加](http://upload-images.jianshu.io/upload_images/6040628-3460d99c5127b5f9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/800 )  
####2. 链接库的搜索位置  
在Searchdirectories ->Linker中添加：  
`/usr/local/bin
/home/xiong/caffe/build/lib`

![链接库](http://upload-images.jianshu.io/upload_images/6040628-261a7ddcbce97a4c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/800)  
####3. 添加需要的链接库名  
在Linkersettings->linker libraries中添加：  
`(CAFFE_ROOT)/build/lib/libcaffe.so`  
在Linkersettings->Other linker options中添加：  
`-pthread  
-lcaffe -lglog -lgflags -lprotobuf -lboost_system -lboost_filesystem  
-lm -lhdf5_hl -lhdf5 -lleveldb -lsnappy -lopencv_core -lopencv_highgui -lopencv_imgproc -llmdb -lboost_thread  
-lstdc++ -lcblas -latlas `  

![链接库名](http://upload-images.jianshu.io/upload_images/6040628-c7756c7af2418391.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/800)  
####4. 添加相关宏定义  
在Compilesettings->#defines中添加：  
`CPU_ONLY
USE_OPENCV
USE_LEVELDB
USE_LMDB`  
####5. 问题汇总  
* 运行报错  
(1)关于缺失libcaffe.so.1.0.0的问题，作者直接将其/home/xiong/caffe/build/lib/libcaffe.so.1.0.0复制到/usr/lib中了，运行没有问题。另外可以自行参考[这里](http://blog.csdn.net/sahusoft/article/details/7388617)
* caffe安装  
可以参考网上资源，有很多ubuntu配置的方法  
-----
####参考  
[ 在ubuntu14.04下使用codeblocks（C++）调试caffe  ](http://blog.csdn.net/geekjzy/article/details/53907556)