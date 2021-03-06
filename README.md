# llvm_tutorials
llvm 教程翻译

## 环境准备
本环境操作系统 是 ubuntu 21.04 

确保你已经安装了 make    
执行环境依赖包初始化    
` cd latex`
` make init_ubuntu `

## 运行
执行    
` make all`   
然后 查看 target 目录下的 内容即可

* [纯中文版pdf](target/pdf/llvm_tutorials_zh.pdf)
* [双语版pdf](target/pdf/llvm_tutorials_mix.pdf)
* [纯中文版md 在线](target/md/llvm_tutorials_zh.md)
* 不可用,目前还无法解决latex转换成md文件时的条件控制 [双语版md 在线](target/md/llvm_tutorials_mix.md)


常用命令 

* 编译 纯中文版 双语版的 pdf   
` make pdf `
 - 编译 纯中文版 pdf    
   ` make zh_pdf `
 - 编译 双语版 pdf    
   ` make mix_pdf `
* 编译 纯中文版 双语版的 md    
` make md `
 - 编译 纯中文版 md   
   ` make zh_md `
 - 编译 双语版 md    
   ` make mix_md `
* 清理临时文件但不清理target 目录    
` make clean `
* 清理所有包括target 目录    
` make cleanall `
* 在gnome下 make all 后在 document viewer 里面打开pdf    
` make view`

## 布局

<pre>
.
├── latex                            //存放latex源代码 目录
│   ├── chapters                     //各个章节存放目录                            
│   │   ├── chapter01.tex
│   │   └── chapter02.tex
│   ├── llvm_tutorials.tex                     //书的入口
│   ├── Makefile                     //
│   └── resources                    // 存放资源文件
│       ├── dot                      // dot 画图的元文件
│       │   └── test.dot
│       ├── images                   // 静态图片 删除了就没有了
│       └── images-gen               // 生成的图片，可以随意删除,会自动生成
│           └── test.svg
├── LICENSE                          // gpl3的授权
├── README.md                        // 本readme
└── target                           //生成物
    ├── md                           //md格式制品
    │   ├── llvm_tutorials_mix.md
    │   ├── llvm_tutorials_zh.md
    │   └── resources
    │       ├── images
    │       └── images-gen
    │           └── test.svg
    └── pdf                          // pdf格式制品
        ├── llvm_tutorials_mix.pdf
        └── llvm_tutorials_zh.pdf

</pre>


## 工作过程
latex 是核心 

## 欢迎来搞
