# Problems-solved

1. （2022.4.25）mmdetection-master从3080上移到2080时，运行test.py报错cuda out of memory，没有具体显示需要多少显存，剩余多少显存。

Solution：mmcv与mmdetection版本不匹配，参照https://github.com/open-mmlab/mmdetection/blob/master/docs/zh_cn/get_started.md

![image](https://github.com/JiaweiLian/Problems-solved/blob/main/mmcv%E4%B8%8Emmdet%E7%89%88%E6%9C%AC%E5%AF%B9%E7%85%A7.png)

2. （2022.4.30）mmdetection训练对抗补丁时模型输出结果没有梯度。

Solution：将mmdet\core\bbox\transforms.py中将预测结果detach的代码注释掉，如下所示：

![image](https://github.com/JiaweiLian/Problems-solved/blob/main/transform.png)

其次将mmdet\core\utils\misc.py中的detach=True改为False，如下所示：

![image](https://github.com/JiaweiLian/Problems-solved/blob/main/misc.png)

3. （2022.5.5）mmdetection单机多卡训练多个程序时，报错：RuntimeError: Address already in use，需要更改tools/dist_train.sh中的端口号（PORT），比如29500改为29501

![image](https://github.com/JiaweiLian/Problems-solved/blob/main/dist_train.png)

4. （2022.7.4）RuntimeError: one of the variables needed for gradient computation has been modified by an inplace operation: [torch.FloatTensor [2, 64, 96, 2]], which is output 0 of SelectBackward, is at version 1; expected version 0 instead.

将inplace操作换为out of place 操作。

![image](https://github.com/JiaweiLian/Problems-solved/blob/main/inplace%20-%20%E5%89%AF%E6%9C%AC.png)
![image](https://github.com/JiaweiLian/Problems-solved/blob/main/out_of_place%20-%20%E5%89%AF%E6%9C%AC.png)

# 5.（2022.9.22）深度学习环境配置

https://blog.csdn.net/Yuan_mingyu/article/details/123927937

还需安装cuda和cudnn，参考问题7

win10本地安装各种包时关掉VPN

 解压.tar.xz文件：tar -xf archive.tar.xz；
 
 各版本cuda下载：直接搜索（如“cuda11.3下载”）；
 
# 6. MMDetection安装
 
 mim install mmcv-full==1.5.0 (按照GitHub教程安装，然后匹配mmcv和mmdet版本即可)
 
# 7. conda创建虚拟环境报错
  
![image](https://github.com/JiaweiLian/Problems-solved/blob/main/conda%E5%88%9B%E5%BB%BA%E8%99%9A%E6%8B%9F%E7%8E%AF%E5%A2%83%E6%8A%A5%E9%94%99.jpg)

解决方法 https://zhuanlan.zhihu.com/p/370524448

# 8. 深度学习环境配置

（1）安装conda和pytorch参照 https://blog.csdn.net/qq_37541097/article/details/120951214

（2）安装cuda和cudnn参照 https://zhuanlan.zhihu.com/p/198161777  https://zhuanlan.zhihu.com/p/476313656

# 9. log文件存在导致cuda安装失败

![image](https://github.com/JiaweiLian/Problems-solved/blob/main/log%E6%96%87%E4%BB%B6%E5%AD%98%E5%9C%A8%E5%AF%BC%E8%87%B4cuda%E5%AE%89%E8%A3%85%E5%A4%B1%E8%B4%A5.jpg)

解决方法：联系服务器管理员删除即可

# 10. 论文上传arXiv问题：

（1）上传bbl文件否则参考文献引用出错（https://blog.csdn.net/Code_Sleep_Eat/article/details/107333551#:~:text=%E4%BD%86%20arxiv%20%E5%9C%A8%E7%BA%BF%20%E7%BC%96%E8%AF%91%20%E8%BF%87%E7%A8%8B%E4%B8%A5%E6%A0%BC%E8%A6%81%E6%B1%82%E4%B8%8D%E8%83%BD%E6%9C%89%E9%94%99%E3%80%82%20%E6%89%80%E4%BB%A5%E7%AC%AC%E4%B8%80%E6%AD%A5%E6%98%AF%E8%A6%81%20%E8%A7%A3%E5%86%B3%20%E5%B7%A5%E7%A8%8B%E4%B8%AD%E5%9B%BA%E6%9C%89%E7%9A%84%E6%8A%A5%E9%94%99%EF%BC%8C%E5%9C%A8overleaf%E4%B8%AD,to%20%60bbl%60%E6%B3%A8%E9%87%8A%E6%8E%89tex%E4%B8%AD%E5%AF%B9bib%E6%96%87%E4%BB%B6%E7%9A%84%E8%AE%BE%E7%BD%AEbbl%20%E6%96%87%E4%BB%B6%E5%86%99%E5%85%A5%E5%9B%BE%E7%89%87%EF%BC%9Aeps%20to%20pdf%E4%B8%80%E4%BA%9B%E5%85%B6%E4%BB%96%E7%9A%84tips%20arxiv%20%E8%B4%A6%E5%8F%B7%E6%B3%A8%E5%86%8C%20arxiv）

（2）图片名中不能有空格，如Faster R-CNN，arXiv会自动将空格转为“_”，但还需将main.tex中的图片名换为变更后的图片名。

（3）( & 等特殊符号也不能有
