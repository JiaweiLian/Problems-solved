# Problems-solved

1. （2022.4.25）mmdetection-master从3080上移到2080时，运行test.py报错cuda out of memory，没有具体显示需要多少显存，剩余多少显存。

Solution：mmcv与mmdetection版本不匹配，参照https://github.com/open-mmlab/mmdetection/blob/master/docs/en/get_started.md

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
