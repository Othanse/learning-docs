# 服装制作规范

## 制作流程：

![img](https://arkimg.ark.online/1688434405220-73.jpeg)

- 请确保各部分环节符合规范。

## 基础规范

### 模型：

<video controls src="https://arkimg.ark.online/03%E8%A7%92%E8%89%B2%E7%AF%87%EF%BC%9A%E4%BA%8C%E6%AC%A1%E5%85%83%E9%A3%8E%E6%A0%BC%EF%BC%88V2%EF%BC%89%E8%A7%92%E8%89%B2%E6%9C%8D%E8%A3%85%E5%88%B6%E4%BD%9C%EF%BC%88%E4%B8%8A%EF%BC%89.mp4" />

- 二次元风格使用**卡通平面渲染**。
- 通过**低模**+**UV规格化**+**引擎材质调整**即可呈现完整效果。
- 无需制作高模和。
- 需要制作贴图。

#### 模型制作

- 建议使用3ds Max制作模型。
- 服装模型分为上装，下装，鞋子，手套四个部件，四部分独立制作。
- 服装部件需要符合换装规则，以便不同服装之间可以切换搭配。
- 皮肤部分和衣服部分使用不同的模型ID。

##### 服装部件制作注意点：

- 材质不支持双面显示，需要通过模复制型实现双面显示。
- 服装遮盖部分的裸模模型需要删掉，服装与裸模衔接的地方需要点对点**焊接**在一起。
- 服装需要对齐裸模布线。

![img](https://arkimg.ark.online/1688983623508-3.png)

- 服装需要对齐裸模拆分线。

![img](https://arkimg.ark.online/1688983659497-10.png)

###### 上装、下装

- 上装，下装模型不够到裸模拆分线位置的，需要用裸模补齐。
- 裸模和服装相接处，顶点需要焊接在一起。

![img](https://arkimg.ark.online/1688983702225-13.png)

###### 鞋子、长袜子

###### 长款：

- 鞋子、袜子长度超过膝盖时，裸模腿脚拆分线以上部分归为**下装部件。**
- 归为下装部件后，最底部布线需要和裸模切口一致（需完全一致）。
- 膝盖和膝盖以下部分需要和裸模布线保持一致。

![img](https://arkimg.ark.online/1688434405213-8.png)

###### 短款：

- 鞋子、袜子长度未过膝盖时，袜子和鞋子拆分为**鞋子部件。**
- 膝盖和膝盖以下部分需要和裸模布线保持一致。
- 模型需要刚刚包裹住腿部裸模。
- 脚的基础裸模可以删掉。

![img](https://arkimg.ark.online/1688983758271-16.png)

###### 裙摆，袖摆，披风

- 需要制作动态骨骼的部分，模型需要单独拆出。
- 切口保持在裸模切口处。
- 动态骨骼部分参考[服装动态骨骼绑定](./3-2-3-Advanced-Dynamic-Component) 。

![img](https://arkimg.ark.online/1688434405213-11.png)

#### 推荐面数：

- 推荐面数包含合并到服装部件上的裸模部分。

|          | 上衣+身体裸模 | 手套+手裸模 | 下装+腿裸模 | 鞋子+脚裸模 |     整套     |
| :------: | :-----------: | :---------: | :---------: | :---------: | :----------: |
| 最大面数 |     2500      |    1800     |    1700     |    1500     | 7500（以内） |

#### 模型命名

- 命名格式：SK_Cartoon _ 性别 _ 部件_ [资源编号](./2-3-2-resource-number) 
- 例如：

  ​	女性上装：SK_Cartoon_Female_Body_ [资源编号](./2-3-2-resource-number) 

  ​	女性下装：SK_Cartoon_Female_Leg_ [资源编号](./2-3-2-resource-number) 

  ​	女性鞋袜：SK_Cartoon_Female_Foot_ [资源编号](./2-3-2-resource-number) 

  ​	女性手套：SK_Cartoon_Female_Hand_ [资源编号](./2-3-2-resource-number) 

- 动态骨骼部分：所接部分命名+Widget

- 例如：

​	 SK_Cartoon_Female_Body _ [资源编号](./2-3-2-resource-number) _Widget

#### 光滑组和模型顶点法线：

- 正确设置光滑组，不能有明显的黑影。

![img](https://arkimg.ark.online/1688434405213-12.png)

- 通过3ds MAX中的Edit Normal功能，统一模型法线。衣服与裙摆，袖摆衔接部分需要统一法线。

- 制作服装时请注意，脖子，手腕处的模型法线需要和裸模保持一致。

![img](https://arkimg.ark.online/1689055661537-4.png)

### UV：

<video controls src="https://arkimg.ark.online/03%E8%A7%92%E8%89%B2%E7%AF%87%EF%BC%9A%E4%BA%8C%E6%AC%A1%E5%85%83%E9%A3%8E%E6%A0%BC%EF%BC%88V2%EF%BC%89%E8%A7%92%E8%89%B2%E6%9C%8D%E8%A3%85%E5%88%B6%E4%BD%9C%EF%BC%88%E4%B8%AD%EF%BC%89.mp4" />

- UV切分线尽量放在不容易看见的位置。
- 服装部分需要多UV来实现，根据功能需求需要制作4个UV。

#### UV1：

- 主要用来制作颜色分块和黑色勾边。

##### 颜色

- 使用共用服装贴图，确认勾边和色块的定位。

![img](https://arkimg.ark.online/1688434405213-15.png)

[共用服装贴图（点此下载）](https://arkimg.ark.online/T_Cartoon_ComResouce_Cloth_ID_001.tga)

- 根据参考图，相同颜色部位的UV放在同样的色块内即可。（如下图）

![img](https://arkimg.ark.online/1688434405213-16.png)

##### 勾边

- 贴图中各个色块周围的黑边是为了制作颜色勾边使用的。
- 通过调节UV的位置和大小来实现黑边的粗细和形状。

![img](https://arkimg.ark.online/1688983902365-22.png)

#### UV2：

- 主要为了后期在引擎中使用材质叠加各种花纹。
- 根据参考图，结合材质的分类，对UV进行色块分类。

![img](https://arkimg.ark.online/1688983926555-25.png)

- 同一区域的UV大小朝向需要保持一致。
- UV不能有拉伸扭曲，服装UV需要根据服装的缝线位置拆分。
- 切缝处UV保持两端对齐。

![img](https://arkimg.ark.online/1688984003308-28.png)

- 相同材质的UV可以重叠，左右对称的物体尽量保持UV重叠。
- UV需要尽量填充满对应色块区域。

![img](https://arkimg.ark.online/1688984018992-31.png)

#### UV3：

- 制作褶皱和一些必要的细节阴影。
- 共用褶皱贴图来制作服装中的褶皱和一些必要的细节阴影。
  - [褶皱一（点此下载）](https://arkimg.ark.online/T_Cartoon_ComResouce_ZheZhou_001.tga)

  - [褶皱二（点此下载）](https://arkimg.ark.online/T_Cartoon_ComResouce_ZheZhou_002.tga)

![img](https://arkimg.ark.online/1688984041307-34.png)

- 通过调整UV的位置和大小来匹配褶皱的形状和位置。

![img](https://arkimg.ark.online/1688984061342-37.png)

- 通过UV的大小，结合褶皱贴图中的渐变部分来制作一些细节阴影，和体积过渡。

![img](https://arkimg.ark.online/1688434405214-30.png)

#### UV4：

- 制作贴花，LOGO。一套服装支持4种贴花。
- 贴花可以公用编辑器资源或自行制作[通用规范](./2-2-2-general-specification) 。
- 把使用相同贴花的UV放在同一颜色区域内。使用下图检查。

[共用服装贴图（点此下载）](https://arkimg.ark.online/T_Cartoon_ComResouce_Cloth_ID_001.tga)

- 可以把贴花贴图放在对应区域内，去验证效果。

![img](https://arkimg.ark.online/1688984089605-40.png)

不使用贴花部分UV缩小到一个点放在0-1象限边角位置。 

### 贴图：

- 贴图使用Tga格式。

#### 贴图命名

- 命名格式：T_Cartoon_ 性别 _ 部件 _[资源编号](./2-3-2-resource-number) 
  -  例如：

  -   女性上装：T_Cartoon_Famle_Body_[资源编号](./2-3-2-resource-number) 

  -   女性下装：T_Cartoon_Female_Leg_[资源编号](./2-3-2-resource-number) 

  -   女性鞋袜：T_Cartoon_Female_Foot_[资源编号](./2-3-2-resource-number) 

  -   女性手套：T_Cartoon_Female_Hand_[资源编号](./2-3-2-resource-number) 

  -  贴图命名需和模型命名保持一致。

#### 贴图制作

- 使用T_Cartoon_ClothBase.psd作为基础贴图模板。

  [贴图模板（点此下载）](https://arkimg.ark.online/T_Cartoon_ClothBase.psd)
- 通过调整四个图层的颜色来制作角色的基础贴图。

  ![img](https://arkimg.ark.online/1691138525441-2.png)
- 通过MAX的平面颜色模式观察效果。

- 贴图通道选择UV1。

  ![img](https://arkimg.ark.online/1691138525440-1.png)

### 材质球：

- 材质命名需符合材质插槽规范。
- 参考[通用规范](./2-2-2-general-specification) 第4部分。

### 顶点色：

<video controls src="https://arkimg.ark.online/03%E8%A7%92%E8%89%B2%E7%AF%87%EF%BC%9A%E4%BA%8C%E6%AC%A1%E5%85%83%E9%A3%8E%E6%A0%BC%EF%BC%88V2%EF%BC%89%E8%A7%92%E8%89%B2%E6%9C%8D%E8%A3%85%E5%88%B6%E4%BD%9C%EF%BC%88%E4%B8%8B%EF%BC%89.mp4" />

- 通过绘制模型顶点色**Alpha通道**的**黑白灰**颜色，可以实现在UE中的模型**外轮廓勾边**的**粗细变化**。
- 建议使用3ds Max制作。

#### 顶点色制作

- 在3ds Max中添加VertexPaint（顶点绘制）工具。
- 选择显示顶点色，设置显示通道为Alpha通道。
- 默认情况，请保持顶点色Alpha为白色。如果不是白色，可以通过油漆桶工具统一覆盖为白色。

![img](https://arkimg.ark.online/1688984186927-43.png)

#### 绘制顶点色Alpha通道

- 选择笔刷，可以绘制颜色。
  - 255白——完全显示勾边
  - 128灰——不显示勾边
  - 0黑——反向显示勾边
- 区间255白-128灰，越靠近灰色，勾边越细。
- 绘制过度颜色，实现沟边粗细变化。

![img](https://arkimg.ark.online/1688984207502-46.png)

#### 绘制完成

- 需要塌陷到可编辑多边形状态或者合并工具，此设置才会被应用。

![img](https://arkimg.ark.online/1688434405214-38.png)

### 资源整理：

#### 模型检查

- 检查3dsMax中单位设置是否是**厘米**。
- 检查模型坐标是否在**世界坐标中心**，并且-Y轴向前。
- 检查资源列表中是否有**无用的模型，空组**等，如果有请删除。
- 检查是否存在错误的双面，破面，破点，5边及以上的多边面。
- 检查部件拆分是否正确，部件包含**上装，下装，手套，鞋袜，前发，后发5**个部分。
- 检查模型命名。
- 检查模型**光滑组**是否设置正确。
- 检查各个衔接部分的**模型法线**，确保和**裸模保持一致**。
- 检查各个部件是否有赋予材质球，并且材质球命名正确。
- 检查UV数量是否正确。

#### FBX输出

- FBX导出设置。
  
  此处导出模型，仅可作为UE验证效果或制作相关贴图使用。
  
  ![img](https://arkimg.ark.online/1688434405214-39.png)

## 换装规范

- 模型切口位置禁止穿插
- 非切口位置因为造型原因可以穿插（比如很长很宽大的手套会超出上衣袖子的范围）

### 换装范围模型下载：

**女性：**

[二次元女性换装范围（点此下载）](https://arkimg.ark.online/%E4%BA%8C%E6%AC%A1%E5%85%83%E5%A5%B3%E6%80%A7%E6%8D%A2%E8%A3%85%E8%8C%83%E5%9B%B4.max)

**男性：**

[二次元男性换装范围（点此下载）](https://arkimg.ark.online/%E4%BA%8C%E6%AC%A1%E5%85%83%E7%94%B7%E6%80%A7%E6%8D%A2%E8%A3%85%E8%8C%83%E5%9B%B4.max)

- **换装规则中的模型仅供范围参考，不作为布线规范或者造型参考使用。**
- 服装部件分为**上装，下装，手套，鞋袜，**以及可能出现的**静态物体**。
- **服装布线尽量和裸模布线一致可避免不必要的穿帮。**

![img](https://arkimg.ark.online/1688434405214-40.png)

### 上装部分

#### 上装**拆分范围**

- 上装范围

![img](https://arkimg.ark.online/1688434405214-41.png)

- 皮带，裤子需要匹配上装范围。
- 皮带，裤子的模型不能超过红色的范围。

![img](https://arkimg.ark.online/1688984266499-49.png)

- 上装部件需被上装范围覆盖。

![img](https://arkimg.ark.online/1688434405215-46.png)

- 手腕关节线必须和上衣范围一致，袖子需包裹手套范围。

![img](https://arkimg.ark.online/1688434405215-47.png)

### 下装部分

#### **下装拆分范围**

- 常规服装布线尽量和裸模布线方向一致可避免不必要的穿帮。

![img](https://arkimg.ark.online/1688984301863-52.png)

- 下装需被皮带范围和裤子范围包裹。
- 皮带需被皮带范围包裹。

![img](https://arkimg.ark.online/1688984315835-55.png)

### 鞋子部分

#### **鞋子拆分范围**

- 所有鞋子都需要被裤子包裹。

![img](https://arkimg.ark.online/1688434405215-53.png)

- 鞋子本身需被鞋靴范围包裹，长靴长袜需和裸模布线保持一致。

![img](https://arkimg.ark.online/1688984340926-58.png)

### 手套部分

#### **手套拆分范围**

- 手套分为长款和短款。
- 短款手套结束在手部切口线位置。
- 长款，短款都不能超出手套范围。

![img](https://arkimg.ark.online/1688984356736-61.png)

### ※※※注意事项※※※

- 如图，外包的袖子没有覆盖手套是错误的。内衣与皮带也有穿插（内衣这里需要做到切口线处，裤子也是。这样可以很好的衔接。）一定要注意我们的层级关系。

![img](https://arkimg.ark.online/1688434405215-58.png)

- 如图，蓝框里面包括了衣服范围和裤子以及腰带范围。这个**范围不能有穿插**。但是裆部及以下的裤子范围因为造型有一定穿插是可以接受的。（**一定要注意裤子有穿插也要覆盖鞋子范围，不能和鞋子长靴范围穿插）**

![img](https://arkimg.ark.online/1688434405215-59.png)

- 如图，鞋带我们需要注意，不论是长靴短靴运动鞋，**鞋带也是不能穿插处鞋子范围**的。可以尽量的贴合到鞋子范围的最大值。

![img](https://arkimg.ark.online/1688434405215-60.png)

**总结：按照层级来看，只有最外的层级在特定情况下可以往外穿插，层级越小越不能穿插。多层范围覆盖的地方也不能穿插。**

#### 实例答疑（精华）

**问：如果我上装的长度超出了提供的长款服装模板，怎么办？**

答：可以超出，但是超出部分需要注意和其他模板搭配时，不能有穿插。并且横段布线尽量和裸模匹配。

**问：这种服装同时有标准长度服装和长款服装特征的怎么办？**

![img](https://arkimg.ark.online/1688434405215-66.png)

答：第一种解决办法，内部贴身部分服装按照标准长度服装，对齐拆分线。外套部分，按照长款服装范围规范制作，外套部分需要保证和所有类型下装无穿插。

![img](https://arkimg.ark.online/1688984415911-67.png)

第二种解决办法，内部贴身部分完全按照长款服装范围制作，外套超出范围部分，需要保证和所有下装范围无穿插。

**问：鞋带很容易造成穿插的模型怎么办？**

答：可以考虑不做蝴蝶结等飞起来的部分，如果很想要蝴蝶结效果，可以考虑直接制作在贴图上。模型部分还是尽量不要有真实的体积感。
