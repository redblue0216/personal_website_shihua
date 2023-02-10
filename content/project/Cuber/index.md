---
title: Cuber-分布式集成学习框架
summary: cuber是一个集成学习框架，主要用于各种集成学习算法的开发，具有灵活动态可配置的特点。cuber主要由三大模块组成，控制引擎、计算引擎和调度引擎。控制引擎依托于networkx的有向无环图技术，需要以计算引擎和调度引擎为基础，运行时加载。计算引擎支持Ray,Dask；调度引擎支持Kahn算法。
tags:
  - machine_learning
date: '2022-10-07T00:00:00Z'

# Optional external URL for project (replaces project detail page).
external_link: ''

image:
  caption: Photo by rawpixel on Unsplash
  focal_point: Smart

links:
  - icon: github
    icon_pack: fab
    name: Follow
    url: https://github.com/redblue0216/Cuber
url_code: ''
url_pdf: ''
url_slides: ''
url_video: ''

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

# Cuber
![shields_version](shields_version.svg)  ![shields_license](shields_license.svg)   ![shields_author](shields_author.svg)  ![shiedls_python](shields_python.svg)

![cuber_avatar](Cuber_avatar.JPG)

## 介绍
+ cuber是一个集成学习框架，主要用于各种集成学习算法的开发，具有灵活动态可配置的特点。cuber主要由三大模块组成，控制引擎、计算引擎和调度引擎。控制引擎依托于networkx的有向无环图技术，需要以计算引擎和调度引擎为基础，运行时加载。计算引擎支持Ray,Dask；调度引擎支持Kahn算法。


## 安装
+ Cuber采用Python开发，得益于Python良好的社区环境，安装支持Pythonic风格的各种管理器。
```bash
$ pip install cuber-0.1-xxxxxxxxxxxx.whl
```



## 快速指南
+ cuber使用主要分为三大步，首先初始化cuber实例，加载计算引擎和调度引擎，获取cuber控制器实例；然后使用装饰器注册目标节点的函数；最后调用cuber控制器执行

+ 以下是cuber主程脚本代码示例：

```python

  ### 载入程序包
  from cuber.interface import Cube
  import time


  ### cuber实例创建
  cuber = Cube(cuber_runner='ray',
               cuber_runner_address='ray://192.168.1.51:10001',
               cuber_scheduler='kahn')


  ### 创建cuber控制器
  cuber_controller = cuber.get_cuber_controller()


  ### 注册目标函数到指定cuber控制器
  @cuber_controller.register(controller_obj=cuber_controller)
  def test_a():
      time.sleep(10)
      print(2)
      return 'a'

  @cuber_controller.register(controller_obj=cuber_controller)
  def test_aa():
      time.sleep(10)
      print(2)
      return 'aa'

  @cuber_controller.register(controller_obj=cuber_controller)
  def test_b():
      time.sleep(10)
      print(2)
      return 'b'

  @cuber_controller.register(controller_obj=cuber_controller)
  def test_bb():
      time.sleep(10)
      print(2)
      return 'bb'

  @cuber_controller.register(controller_obj=cuber_controller)
  def test_c():
      time.sleep(10)
      print(2)
      return 'c'

  @cuber_controller.register(controller_obj=cuber_controller)
  def test_cc():
      time.sleep(10)
      print(2)
      return 'cc'

  @cuber_controller.register(controller_obj=cuber_controller)
  def test_d():
      time.sleep(10)
      return 'd'


  ### 注册目标函数依赖关系到指定cuber控制器
  test_a >> test_b >> test_c >> test_d
  test_aa >> test_b >> test_d
  test_bb >> test_c >> test_d
  test_cc >> test_d


  ### 展示节点和边情况
  print('~~~~~~',cuber_controller.get_graph_obj())
  print('------',cuber_controller.show_nodes())
  print('======',cuber_controller.show_edges())


  ### 使用二级统一API
  time_start = time.time()
  exec_result = cuber_controller.execute()
  time_end = time.time()
  print('============================== Parallel function running',time_end - time_start)


  ### 串行函数运行
  time_start = time.time()
  test_a()
  test_aa()
  test_bb()
  test_cc()
  test_b()
  test_c()
  test_d()
  time_end = time.time()
  print('============================== Serial function operation',time_end - time_start)
```


## 设计
+ 大量使用元编程技术，提高代码灵活性、可读性和维护质量
+ 设计了控制引擎、计算引擎和调度引擎，实现灵活动态可扩展
+ 天然支持分布式
+ 三级API设计，使用方便，适应不同程度的使用人员
+ 技术列表
  + __new__技术
  + __init__技术
  + __prepare__技术
  + __call__技术
  + type元类
  + 描述符技术
  + Mixin
  + 装饰器技术
  + namedtuple
  + Networkx
  + FSM-transitions
  + 运算符重载
  + __slots__技术
  + Ray







