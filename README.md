# Sass
Learn about Sass

##安装
1.安装Ruby到你的操作系统。安装过程中请注意勾选Add Ruby executables to your PATH添加到系统环境变量。
安装完成后需测试安装有没有成功,运行CMD输入以下命令：
```
ruby -v
//如安装成功会打印
ruby 2.2.2p95 (2015-04-13 revision 50295) [i386-mingw32]
```

2.更换gem源
```
//1.删除原gem源
gem sources --remove https://rubygems.org/

//2.添加国内淘宝源
gem sources -a https://rubygems.org/

//3.打印是否替换成功
gem sources -l

//4.更换成功后打印如下
*** CURRENT SOURCES ***
https://ruby.taobao.org/
```

3.安装Sass和Compass
```
//安装如下(如mac安装遇到权限问题需加 sudo gem install sass)
gem install sass
```

4.常用命令
```
//更新sass
gem update sass

//查看sass版本
sass -v

//查看sass帮助
sass -h
```


##编译Sass
####命令行编译
```
//单文件转换命令
sass input.scss output.css

//单文件监听命令
sass --watch input.scss:output.css

//如果你有很多的sass文件的目录，你也可以告诉sass监听整个目录：
sass --watch app/sass:public/stylesheets
```

####命令行编译配置选项
命令行编译sass有配置选项，如编译过后css排版、生成调试map、开启debug信息等，可通过使用命令sass -v查看详细。我们一般常用两种--style``--sourcemap。
```
//编译格式
sass --watch input.scss:output.css --style compact

//编译添加调试map
sass --watch input.scss:output.css --sourcemap

//选择编译格式并添加调试map
sass --watch input.scss:output.css --style expanded --sourcemap

//开启debug信息
sass --watch input.scss:output.css --debug-info
```
* --style表示解析后的css是什么排版格式;
sass内置有四种编译格式:nested``expanded``compact``compressed。
* --sourcemap表示开启sourcemap调试。开启sourcemap调试后，会生成一个后缀名为.css.map文件。

####四种编译排版演示;
```
//未编译样式
.box {
  width: 300px;
  height: 400px;
  &-title {
    height: 30px;
    line-height: 30px;
  }
}
```
#####nested 编译排版格式
```
/*命令行内容*/
sass style.scss:style.css --style nested

/*编译过后样式*/
.box {
  width: 300px;
  height: 400px; }
  .box-title {
    height: 30px;
    line-height: 30px; }
```
#####expanded 编译排版格式
```
/*命令行内容*/
sass demo.scss:demo.css --style expanded

/*编译过后样式*/
.box {
  width: 300px;
  height: 400px;
}
.box-title {
  height: 30px;
  line-height: 30px;
}
```
#####compact 编译排版格式
```
/*命令行内容*/
sass style.scss:style.css --style compact

/*编译过后样式*/
.box { width: 300px; height: 400px; }
.box-title { height: 30px; line-height: 30px; }
```
#####compressed 编译排版格式
```
/*命令行内容*/
sass style.scss:style.css --style compressed

/*编译过后样式*/
.box{width:300px;height:400px}.box-title{height:30px;line-height:30px}
```