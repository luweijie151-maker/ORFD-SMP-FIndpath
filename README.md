## 项目简介

基于 [ORFD](https://github.com/chaytonmin/ORAD-3D-Dataset-For-Off-Road-AD) 越野路面数据集，使用 [SMP](https://github.com/qubvel-org/segmentation_models.pytorch)（Segmentation Models PyTorch）完成地表语义分割，将分割预测结果转换为栅格占用地图，通过 A\* FindPath 算法实现越野场景自主路径规划。

## 环境依赖
核心依赖：

- pytorch
- segmentation-models-pytorch
- opencv-python
- numpy
- matplotlib

```

## 运行流程

1. 使用训练好的 ORFD 分割模型对路面图像推理，输出分割掩码
2. 将多类别分割掩码二值化为可通行 / 障碍物栅格地图
3. 载入栅格地图，调用 FindPath（A\*）算法生成最优行驶路径
4. 可视化分割图与规划路径结果

## 模型说明

训练权重文件`.ckpt`体积较大，不存入仓库，可自行训练或网盘下载模型放入本地`weights/`文件夹。

## 安装第三方库 SMP

无需存放源码文件夹，直接 pip 安装：

```
pip install segmentation-models-pytorch
```

## 仓库规范

1. 不存储训练权重、大型模型文件
2. 第三方依赖统一通过 requirements 安装
3. 仅保留项目自研代码、脚本与可视化工具

## 使用方法

1. 配置环境依赖
2. 将模型权重放置本地 weights 目录
3. 运行 scripts 内推理脚本生成分割结果
4. 执行栅格转换脚本得到栅格地图
5. 运行路径规划脚本输出导航路径

## 结果展示
## 结果展示
<div align="center">
<video width="700" controls>
  <source src="output.mp4" type="video/mp4">
  浏览器不支持视频播放，请下载查看
</video>
<br>
ORFD语义分割转栅格图+A\*路径规划完整演示
</div>
