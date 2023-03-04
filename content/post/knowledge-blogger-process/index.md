---
title: 知识博主流程
subtitle: 这是一个知识博主流程简介文档

# Summary for listings and search engines
summary: 这是一个知识博主流程简介文档
# Link this post with a project
projects: []

# Date published
date: '2023-03-04T00:00:00Z'

# Date updated
lastmod: '2023-03-04T00:00:00Z'

# Is this an unpublished draft?
draft: false

# Show this page in the Featured widget?
featured: false

# Featured image
# Place an image named `featured.jpg/png` in this page's folder and customize its options here.
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/CpkOjOcXdUY)'
  focal_point: ''
  placement: 2
  preview_only: false

authors:
  - admin
  - wowchemy

tags:
  - 工作
  - 个人文档

categories:
  - 工作
  - 个人文档
---


## book类
+ Step1：staratlas工作空间下编写内容草稿
+ Step2：将内容草稿按照mdbook的格式添加到workspace工作空间
  + 注意不要忘记修改.gitignore文件，将book文件夹暴露出来
+ Step3：在github上创建新的项目
+ Step4：在本地的mdbook空间下创建git，并添加readme文件
+ Step5：在mdbook文件夹下使用mdbook  build生成静态文件(book文件夹下）
+ Step6：将本地git上传至github
+ Step7：使用netlify将github库发布出去
## post类
+ Step1：staratlas工作空间下编写内容草稿
+ Step2：将内容草稿按照wowchemy的格式添加到workspace工作空间perjsonal_website
+ Step3：将本地personal_wbsite的git上传到github上
+ Step4：检查netlify是否自动更新