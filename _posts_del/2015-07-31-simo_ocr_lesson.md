---
layout: post
title: " 个人OCR学习使用 "
date: 2015-07-31 14:20
category : tech
---
            几年前接触ocr的东西，没有正式使用，只训练了几组中文字库就略过了。这次朋友正好用到，重温一边，软件和过程都整理文档方便备用。真正要做到ocr高识别，必须精通算法和神经网络。此篇为外行浅入，玩玩总可以吧。
            感谢tesseract的开源，感谢google的各种支持，感谢网友们无私的文档奉献。

**语言、编译环境**

* java 
* python（2.7） pip PIL

**软件介绍**
			![ocr soft list and the docs](/public/image/ocr-soft.png)
			![ocr soft](/public/image/ocr-soft1.png)

* tesseract 30年前HP的开源的作品，后来google接管了。ocr不二的推荐。
* jTessBoxEditor 库文件编辑工具
* css222.py 图片二值化脚本，针对rgb值，还能再优化。
* ttf2box.bat ttf文件调用tesseract命令
* create.bat 最终生成训练库文件的脚本

* tesseract 
    * 下载地址：https://code.google.com/p/tesseract-ocr/downloads/list
* jTessBoxEditor 训练工具
    * http://sourceforge.net/projects/vietocr/files/jTessBoxEditor/

**操作流程**

1. 使用jTessBoxEditor拼合库文件， 格式ttf
2. 通过css222.py 进行二值化
3. 通过ttf2box.bat 生成box文件
4. 创建必须文件，参考文档。 font啊，charset啊等等
5. 通过create.bat生成最终库文件 (比如叫 abc.库文件后缀)
6. 把库文件导入tesseract的库目录
7. 识别：通过tesseract 目标文件 结果文件 -l abc
