# Compilers_Java
Learn Compilers through creating a compiler for java
### @背景介绍:
        这学期学习编译原理这门课,发现上课内容很枯燥,老师将的理论知识大多很难理解,在知乎网站上看到
        有些网友说边学边自己写个编译器有助于对课本知识的理解,加上自己的编程能力还不是很好,想利用
        休闲时间自己弄个编译Java语言的编译器,努力坚持完成这个目标.加油!<另外>参考了另一个网友写
        的项目,网址https://github.com/Xiang1993/jack-compiler/blob/master/README.md
### @Java语言介绍

### java语言要素
    l1保留字
    l2标识符
    l3常量
    l4运算符
    l5注释符
## 词法分析器
    词法单元划分表,例如
    读入词素输入流,建立缓冲区,缓冲区中维护两个指针,一个指向当前词素的开始处(lexemeBegin),
    一个向前扫描词素的指针(forward),该指针的算法如下:
    ```java(伪代码)
       switch(*forward){
         case eof:
                if(forward在第一个缓冲区的末尾处){
                   装载第二个缓冲区;
                   forward=第二个缓冲区的开头;
                }
                else if(forward在第二个缓冲区末尾){
                    装载第一个缓冲区;
                    forward=,,第一个缓冲区的开头;
                }
                else
                  eof表示输入字符串的,结束,
                  (!!!配对当前词素终,返回词素属性值)
                  终止词法分析
                
                break;
                若其他字符(forward!=eof)情况
       }
       
    ```
    
