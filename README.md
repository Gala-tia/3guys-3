## DCGAN：Deep Convolutional Generative Adversarial Networks模型在pytorch当中的实现
---

### 目录
1. [所需环境 Environment](#所需环境)
3. [文件下载 Download](#文件下载)
4. [预测步骤 How2predict](#预测步骤)
5. [训练步骤 How2train](#训练步骤)
6. [参考资料 Reference](#Reference)

## 所需环境
pytorch==1.2.0  

## 文件下载
权值的百度网盘地址如下：    
链接：https://pan.baidu.com/s/1qn_po_OAsaVf38Obbnau3g 提取码：c7zy  

数据集可以通过百度网盘下载：   
链接：https://pan.baidu.com/s/1qn_po_OAsaVf38Obbnau3g 提取码：c7zy  

## 预测步骤
### a、使用预训练权重
1. 下载完库后解压，直接运行predict.py，输入要提高分辨率的图片的路径，即可生成高分辨率图片，生成图片位于results/predict_out/predict_srgan.png。如输入：
```python
img/before.jpg
```
### b、使用自己训练的权重 
1. 按照训练步骤训练。    
2. 在srgan.py文件里面，在如下部分修改model_path使其对应训练好的文件；**model_path对应logs文件夹下面的权值文件**。    
```python
_defaults = {
    #-----------------------------------------------#
    #   model_path指向logs文件夹下的权值文件
    #-----------------------------------------------#
    "model_path"        : 'model_data/Generator_SRGAN.pth',
    #-----------------------------------------------#
    #   上采样的倍数，和训练时一样
    #-----------------------------------------------#
    "scale_factor"      : 4, 
    #-------------------------------#
    #   是否使用Cuda
    #   没有GPU可以设置成False
    #-------------------------------#
    "cuda"              : True,
}
```
3. 运行predict.py，输入要提高分辨率的图片的路径，即可生成高分辨率图片，生成图片位于results/predict_out/predict_srgan.png。 

## 训练步骤
1. 训练前将期望生成的图片文件放在datasets文件夹下（参考Yahoo MirFlickr25k数据集）。  
2. 运行根目录下面的txt_annotation.py，生成train_lines.txt，保证train_lines.txt内部是有文件路径内容的。  
3. 运行train.py文件进行训练，训练过程中生成的图片可查看results/train_out文件夹下的图片。  


