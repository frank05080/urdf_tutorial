sudo apt install ros-humble-urdf-launch
sudo apt install ros-humble-joint-state-publisher

display.launch.py actually runs the two launch files under /opt/ros/humble/share/urdf_launch/launch

## First Example

在URDF (Universal Robot Description Format) 中，`<robot>` 元素定义了一个或多个相互连接的`<link>`元素以及它们之间的`<joint>`元素。每个`<link>`代表机器人的一个部件，可以有自己的形状、尺寸、质量和惯性属性。在给出的URDF片段中，定义了一个名为`base_link`的单独`<link>`，该`<link>`具有一个视觉（`<visual>`）元素，该元素描述了`<link>`的可视化表示方式。

这段URDF定义了一个名为`myfirst`的机器人，它只有一个名为`base_link`的链接。这个`<link>`包含一个视觉元素，表示为一个圆柱体，圆柱体的长度为0.6米，半径为0.2米。

在RViz或其他可视化工具中，`fixed frame`是一个参考坐标系，其他所有元素都是相对于它定位的。在此示例中，`base_link`作为唯一的`<link>`，自然被用作`fixed frame`。这意味着它是场景中所有变换和定位的参考点。

关于圆柱体的可视化和它相对于网格的位置，以下几点值得注意：

1. **圆柱体的原点**：在URDF中定义的视觉元素（在这个例子中是一个圆柱体）默认情况下其原点位于其几何中心。这意味着圆柱体的中心（长度上的中点）位于其原点。

2. **圆柱体相对于网格的位置**：由于圆柱体的原点（也是`base_link`的原点）位于圆柱体的中心，而这个原点又被用作RViz中的`fixed frame`的中心，所以圆柱体的一半会位于这个网格（假设网格在原点）的上方，另一半位于网格的下方。这是因为圆柱体的原点位于其几何中心，而这个原点恰好位于`fixed frame`的中心。

这样的表示方法使得在可视化和理解机器人模型及其组件在空间中的相对位置时更加直观。如果你在RViz中查看这个模型，你会看到圆柱体一半在地面（网格）上方，另一半在地面下方，因为它的中心与`fixed frame`的中心对齐。

## Second Example

If not set origin in joints, the origin of base_link and right_leg are overlapping

![](./imgs/1.JPG)
![](./imgs/2.JPG)