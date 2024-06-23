---
layout: blog
title: Unity插件Dialogue System for unity使用记录
date: 2023-05-12 10:02:31
categories:
  - Skill
  - Unity
tags:
  - Game
  - Dialogue System for unity
  - Unity
  - Chinese 中文
---

最近的毕业设计项目创作过程中，选用了Dialogue System for unity插件来实现游戏的对话系统，对于一些细节的教程在网络上找了很久也没找到orz，在此记录当时迷茫了很久的几个点。

# NPC头像的更改

1. 打开对应的**dialogue database**

![dialogue database](image-20230512101741139.png)

2. 点击对应的想要**更改头像的NPC**

![更改头像的NPC](image-20230512101802916.png)

3. 在inspector面板出现对应属性，更改**portrait textures**即可

![portrait textures](image-20230512101956715.png)

# 对话UI的更改

1. 打开想要更改的对应**UI预制体**。

2. 与美术小伙伴沟通，更改组件布局。下图是初始的basic dialogue system UI面板。
   ![UI预制体](image-20230512102503171.png)
   我们想要的UI效果如图.
   ![想要的UI效果](image-20230512102622755.png)
   和美术小伙伴沟通确定UI的布局，对NPC和玩家的对话框位置进行调换。

3. 对对话框进行美化。

   * NPC部分

     * **底图更换。**更改portrait image的spirit。

       ![portrait image](image-20230512103354589.png)

       需要勾选如下：

       ![portrait image2](image-20230512110957945.png)

     * **NPC头像更换。**用上文所示方法，在database更换人物头像。

     * **NPC与底图更换。**因为美术给每个NPC都绘制了不同的对话框，所以最后选择对话框和人物立绘一起在portrait textures进行更换。不过统一尺寸又很难……所以只能在ps慢慢调整了。

     * 更改图像与文字排版。取消勾选pc subtitle panel的horizontal layout group

       ![horizontal layout group](image-20230512111831437.png)

       调整好文字与图像位置后再重新勾选.

   * 玩家部分。

     * 更改scroll rect的spirit。

       ![scroll rect](image-20230512111622101.png)

       ![scroll rect2](image-20230512111734094.png)

     * **文字部分**。

       更改**文字排版**。需要取消勾选更改scroll rect、Response Button Template的Vertical Layout Group。更改后再重新勾选。

       因为文字部分涉及到**选项分布**，所以排布的参数需要微调。这是下列参数展现的最终效果。

       ![最终效果](image-20230512112922091.png)

       ![最终效果明显显示](image-20230512113011077.png)

       红框中是可能影响到选项排布的**参数**：

       ![参数](image-20230512113040001.png)

       ![参数2](image-20230512113128552.png)


最后想说一个和文章没什么关系的感想，好的UI真的要和美术一点点磨合……确定图层关系和控制贴图的形状需要漫长的沟通。
