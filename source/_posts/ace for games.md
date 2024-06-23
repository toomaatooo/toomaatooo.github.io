---
title: ACE(Avatar Cloud Engine) for Games在UE5中的使用
date: 2023-07-19 00:14:53
categories:
  - Game
  - Program
tags:
  - Game
  - Unity
  - UE5
  - NVIDIA
  - AI
  - Chinese 中文
---

阅读文章[Introducing NVIDIA ACE For Games - Spark Life Into Virtual Characters With Generative AI | GeForce News | NVIDIA](https://www.nvidia.com/en-us/geforce/news/nvidia-ace-for-games-generative-ai-npcs/)后决定实践该技术流程

该模型可以实现与游戏NPC实时对话，具体流程为：

- 利用NVIDIA'NeMo AI框架结合NPC个人背景生成其“专属台词”
- 利用NVIDIA'Rica模型进行语音识别和文本转语音
- 利用NVIDIA'Omniverse Audio2Face功能结合文本驱动数字人面部表情

该模型目前已支持在Unity和UE5中使用，但本人没有在Unity中成功尝试，在此提供在UE5中的使用流程。文末附已知Unity可用流程。

# 安装插件

## 下载插件并安装

- Convai Unreal 插件仅与Unreal Engine 5和4.26 或更高版本兼容

- 在链接中下载对应版本的插件[文件夹 ](https://drive.google.com/drive/u/0/folders/1bhWisnnlD-gfeo5QQ65Tpbl_GMXoFoc-)[- Google ](https://drive.google.com/drive/u/0/folders/1bhWisnnlD-gfeo5QQ65Tpbl_GMXoFoc-)[云端硬盘](https://drive.google.com/drive/u/0/folders/1bhWisnnlD-gfeo5QQ65Tpbl_GMXoFoc-)

- 找到引擎的插件安装目录UE_5.2>Engine>Plugins

  ![解压后的层级关系](image-20230718215419330.png)

## 在引擎中激活插件

- 打开引擎
- 创建第一人称游戏项目
- 在编辑中打开插件，搜索convai，勾选后选择立即重启。![操作如图](image-20230718215649123.png)

- 找到项目所在文件夹,打开Config/DefaultEngine.ini,在文件顶端增加

  ```
  [Voice]
  bEnabled=true
  ```

- 保存之后关闭,重新启动引擎

# 创建定制角色

- 在网站[Loading... (convai.com)](https://convai.com/pipeline/dashboard)注册并登录
- 点击 create a new character
  ![创建新角色](image-20230718232237640.png)

- 填写合适的数据，右侧的人物也可以进行形象定制。![对人物进行形象定制](image-20230718232348260.png)

- 记录角色的Character’s ID和API Key，后续在引擎中需要使用。

  ![Character’s ID](image-20230718232438909.png)
  ![API Key](image-20230718232533250.png)

# 引擎中导入角色信息

## 输入API Key

- 打开引擎，编辑-项目设置-插件-convai
- 刚才在页面复制的API Key![输入API](image-20230718232613620.png)

## 创建蓝图

- 右键内容浏览器，创建蓝图类

  ![创建蓝图类](image-20230718232827669.png)

- 输入搜索ConvaiBaseCharacter

  ![创建蓝图类](image-20230718232903458.png)

- 将蓝图拖拽至场景中

  ![将蓝图拖拽至场景中](image-20230718232959994.png)

## 修改蓝图

- 大纲中找到TestChar，细节-默认更改Char ID![更改Char ID](image-20230718233158238.png)

- 修改Blueprints文件夹中BP_FirstPersonCharacter蓝图

  ![BP_FirstPersonCharacter蓝图](image-20230718233343050.png)

- 更改类设置中的类选项-父类为ConvaiBasePlayer![更改类设置中的类选项-父类为ConvaiBasePlayer](image-20230718233523020.png)

- 目前为止在场景里面可以和NPC正常对话，只是看不到模型，请确保到这一步运行时无bug

# 导入角色模型

## 下载模型

- 打开窗口-Quixel Bridge.![窗口-Quixel Bridge](image-20230718233728429.png)

- 下载喜欢的模型，然后导入
  ![下载模型](image-20230718233801181.png)![导入模型](image-20230718233855307.png)

- 对话框勾选启用缺失

  ![勾选如图](image-20230718233915357.png)

- 此时引擎提示重启，请按提示重启 

## 角色导入场景

- 在内容管理器中选择角色对应的文件夹。选择了哪个角色，该文件夹就是什么名字。
- 将本蓝图类拖入之后场景会出现角色![文件夹选取与角色拖入](image-20230718234203261.png)

- 双击本蓝图类进行编辑
- 更改类设置中的类选项-父类为Convai Base Character![编辑本蓝图类](image-20230718234433365.png)

- 更改组件-Body-动画-动画类为Convai_MetaHuman_BodyAnim![Convai_MetaHuman_BodyAnim](image-20230718234543054.png)
- 更改组件-Body-Face-动画-动画类为Convai_MetaHuman_FaceAnim
  ![Convai_MetaHuman_FaceAnim](image-20230718234659515.png)
- 完成后进行编译，确保没有报错

## 配置人物

- 点击场景中的人物，细节-默认-Char ID中粘贴网站复制的ID
  ![更改Char ID](image-20230718235007891.png)

到此为止已完成所有配置，可以实现Youtube视频中所展示的效果。

# 在Unity中使用

适用于windows系统与2019.4LTS以上版本Unity

- 下载core unity plugin[ConvaiforUnity-v2023.05.11-core.unitypackage - Google ](https://drive.google.com/file/d/1co7z0qMg9N_teYR2dQY5mEyof1kDIMCs/view)[云端硬盘](https://drive.google.com/file/d/1co7z0qMg9N_teYR2dQY5mEyof1kDIMCs/view)

- 下载所需ConvaiforUnity_vX.Y.Z.unitypackage https://convai.com/download/UnityPlugin

- 按照《创建定制角色》在convai网站中完成操作

- 导入package与plugin
- 在edit-ProjectSettings-Player-other Settings取消勾选Assemble Version Validation
- Convai-Convai Setup中输入API密钥
  ![输入API密钥](image-20230718235640018.png)
  ![输入API密钥](image-20230718235655348.png)

- 打开assets-convai-scenes中场景，更改Convai NPC Ellen-Convai NPC (Script)-Character ID角色ID
  ![更改角色ID](image-20230718235747800.png)

以下步骤为可能需要

> - 添加插件[NPC AI - Dialog, actions and general intelligence - by ](https://assetstore.unity.com/packages/tools/ai/npc-ai-dialog-actions-and-general-intelligence-by-convai-235621)[Convai](https://assetstore.unity.com/packages/tools/ai/npc-ai-dialog-actions-and-general-intelligence-by-convai-235621)[ | AI | Unity Asset Store](https://assetstore.unity.com/packages/tools/ai/npc-ai-dialog-actions-and-general-intelligence-by-convai-235621)
> - 添加后在unity打开，download 之后 import
> - 弹出tmp importer的时候只勾选Import TMP Essentials 安装完毕之后直接退出