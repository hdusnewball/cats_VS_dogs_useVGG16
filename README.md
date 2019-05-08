# cats_VS_dogs_useVGG16
# 用Vgg16训练 猫狗数据集
## 在不用vgg的情况下
1.20000张图片训练 大概能达到0.86   2000张 0.68
2.用vgg之后20000张能达到0.94

##  改进方向 
1.将图片进行乱序   但因为原数据为cat.1.jpg  我取数据的方式是这样的
~~~
'cat.{}.jpg'.format(i) for i in range(10000)   
'dog.{}.jpg'.format(i) for i in range(10000)   
#考虑用如下方式进行乱序
index = np.random.permutation(20000)     #猫加狗一共20000
~~~
但问题是：在保证分类标签不变的情况下如何将猫与狗之间相互交叉  
即如何在猫放在一个文件夹  狗放在一个文件夹的   情况下将猫狗穿插训练
2.在最后增加全连接层以及增加BatchNormalization

model.add(layers.BatchNormalization())

BN一般添加在conv2D之后 和 Dense层之后 用于。。。没完全理解透
这是这里的详细解释[batchnormalization](https://www.cnblogs.com/guoyaohua/p/8724433.html)
