# aws ec2上体验rust

rust是与c相竞争又相补充的语言，内存、线程安全，并发友好，高效，在某些需要c而又不涉及传统操作系统底层的地方，用的很多。

## 在aws ec2上体验rust:
### 创建一个基于aws amzn2 linux的ec2, 登录

    sudo yum update
    curl https://sh.rustup.rs | sh #安装rustup环境管理器
    source $HOME/.cargo/env #按提示，把cargo bin加到PATH

### 开始我们的hello word: 创建hw.rs，内容如下：

    fn main(){
      println!("hw");
    }

编译：rustc hw.rs  
出现错误：linker 'cc' not found (同时，当前目录生成了很多.o中间文件，没有得到link所以没有清除)  
安装gcc解决问题：sudo yum install gcc  
再编译，生成名为hw的可执行文件，大小3M多。.o文件消失。

### 运行：./hw，完成。
