# YOLO-3D

这是一个实时3D物体检测系统，将用于物体检测的YOLOv11与用于深度估计的Depth Anything v2相结合，从而生成伪3D边界框并实现BEV可视化。

## 项目结构

```
YOLO-3D/

│── run.py                  # 主脚本
│── detection_model.py      # YOLOv11 目标检测
│── depth_model.py          # Depth Anything v2 深度估计
│── bbox3d_utils.py         # 3D 边界框
│── load_camera_params.py   # 相机参数
├── requirements.txt            # 项目依赖
└── README.md                   
```

## 特点

- 使用 YOLOv11 进行实时目标检测
- 使用 Depth Anything v2 进行深度估计
- 3D 边界框可视化
- 鸟瞰视图 (BEV) 可视化
- 目标跟踪功能
- 支持视频文件和摄像头实时输入
- 可调节模型大小，以在性能与精度之间进行权衡

## 依赖

- Python 3.8+
- PyTorch 2.0+
- OpenCV
- NumPy
- 其他依赖在 `requirements.txt` 中

## 下载

1. 克隆此仓库:
   ```
   git clone https://github.com/Lao-G-G/YOLO-3D.git
   cd YOLO-3D
   ```

2. 安装依赖:
   ```
   pip install -r requirements.txt
   ```

3. 下载模型权重（首次运行时将自动下载）

## 使用

运行主脚本：

```bash
python run.py
```

[演示视频](https://www.bilibili.com/video/BV1yMjt6bERJ/?spm_id_from=333.1387.homepage.video_card.click&vd_source=fb87b423284d2be4e618a494abc962ca)

### 配置选项

您可以在 `run.py` 修改以下参数： :

- **输入/输出**:
  - `source`: 输入视频文件或网络摄像头的路径索引（0 表示默认摄像头）
  - `output_path`: 输出路径

- **模型选择**:
  - `yolo_model_size`: YOLOv11 模型大小 ("nano", "small", "medium", "large", "extra")
  - `depth_model_size`: Depth Anything v2 模型大小 ("small", "base", "large")

- **检测设置**:
  - `conf_threshold`: 物体检测的置信阈值
  - `iou_threshold`: NMS的IOU阈值
  - `classes`: 按类过滤，例如：[0, 1, 2] 表示特定类，None 表示所有类

- **功能开关**:
  - `enable_tracking`: 目标跟踪
  - `enable_bev`: BEV可视化
  - `enable_pseudo_3d`: 3D可视化



## 工作流

1. **目标检测**：YOLOv11 检测画面中的目标并提供 2D 边界框
2. **深度估计**：Depth Anything v2 为整个画面生成深度图
3. **3D 边界框估计**：将 2D 边界框与深度信息结合，生成 3D 边界框
4. **可视化**：渲染 3D 边界框和俯视图，以更好地理解空间关系


## 致谢

- YOLOv11 by Ultralytics
- Depth Anything v2 by Microsoft 
