# Problems-solved

1. （2022.4.25）mmdetection-master从3080上移到2080时，运行test.py报错cuda out of memory，没有具体显示需要多少显存，剩余多少显存。

Solution：mmcv与mmdetection版本不匹配，参照https://github.com/open-mmlab/mmdetection/blob/master/docs/en/get_started.md

![image](https://github.com/JiaweiLian/Problems-solved/blob/main/mmcv%E4%B8%8Emmdet%E7%89%88%E6%9C%AC%E5%AF%B9%E7%85%A7.png)

2. （2022.4.30）mmdetection训练对抗补丁时模型输出结果没有梯度。

Solution：将mmdet\core\bbox\transforms.py中将预测结果detach的代码注释掉，如下所示：

![image](https://github.com/JiaweiLian/Problems-solved/blob/main/transform.png)

其次将mmdet\core\utils\misc.py中的detach=True改为False，如下所示：

![image](https://github.com/JiaweiLian/Problems-solved/blob/main/misc.png)
