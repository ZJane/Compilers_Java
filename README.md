# Compilers_Java
Learn Compilers through creating a compiler for java
### @背景介绍:
        这学期学习编译原理这门课,发现上课内容很枯燥,老师将的理论知识大多很难理解,在知乎网站上看到
        有些网友说边学边自己写个编译器有助于对课本知识的理解,加上自己的编程能力还不是很好,想利用
        休闲时间自己弄个编译Java语言的编译器,努力坚持完成这个目标.加油!<另外>参考了另一个网友写
        的项目,网址https://github.com/Xiang1993/jack-compiler/blob/master/README.md
### @Java语言介绍

### java语言要素
####   l1保留字
    java中共有50个保留字
    import,package,class,abstract,extends,implements,
    private,protected,public,synchronized,transient,volatile,
    new,super,this,throw,throws,try,static,void,default,
    final,finally,return,native,instanceof,null,
    byte,int,boolean,char,double,float,long,short,
    case,switch,catch,continue,do,else,for,if,while
    false,true, break,
   
####    l2标识符
    令L={a,b,c,d,...A,B,C,D...},D={0,1,2,3,4,5,6,7,8,9}
    则L(LUD)*表示由字母开头的,字母和数字组成的串的集合,此集合
    等同于java中的标识符(id)
###    l3常量a
    constant,包括数值  量,整型,浮点型,字节,等.(包括逻辑常量:false和true),f字符常量'a'等

####    l4运算符
     <  >   <= >=   + - *  /   ! &  !=  ||  |  >>  <<   -- ++   +=    %  ^
     标点符号:   "  "   {  }  [   ]   ,  '   '
     
     
####    l5注释符
## 词法分析器
    词法单元划分表,例如
    | 词素  |  词法单元   |属性值 |
    |100    |number(int) |整数值
    |return |return|
    |if     |if           |不需要保留字的属性值
    |float  |float        |
    |=      |assign_op(赋值号)|
    |lexer  |id(标识符)   |指向符号表中lexer的 指针
    <id,指向符号表中lexer的指针>
    <assign_op>
    <return>
    <number,2>
    
    (参考编译原理龙书第二版第72页,3页)读入词素输入流,建立缓冲区,缓冲区中维护两个指针,一个指向当前词素的开始处(lexemeBegin),
    一个向前扫描词素的指针(forward),该指针的算法如下:
  
``` 
``java``(伪代码)
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
    
