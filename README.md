## 在线的Markdown编辑器
```
http://mahua.jser.me/
```

# SASS
```
https://www.sass.hk/
```

# Ubuntu安装Sass.
## 安装ruby
```
sudo apt install ruby
```

## 查看ruby版本
```
ruby -v
```

## 安装sass
```
sudo gem install sass
```

## 查看sass版本
```
sass -v
```

## 安装compass
```
sudo apt install ruby-compass
```

## 查看compass版本
```
compass -v
```

## 更新sass
```
gem update sass
```

## 查看sass版本
```
sass -v
```

## 查看sass帮助
```
sass -h
```

# 编译sass(*).
```
概述：sass编译有很多种方式，如命令行编译模式、sublime插件SASS-Build、编译软件koala、前端自动化软件codekit、Grunt打造前端自动化工作流grunt-sass、Gulp打造前端自动化工作流gulp-ruby-sass等.
```

## 命令行编译.
### 单文件转换命令
```
sass input.scss output.css
```

### 单文件监听命令
```
sass --watch input.scss:output.css
```

### 实例
```
sudo sass --watch test.scss:test.css
```

### 如果你有很多的sass文件的目录，你也可以告诉sass监听整个目录：
```
sass --watch app/sass:public/stylesheets
```

### 实例
```
sudo sass --watch sass/css:static/css --style expanded
```

### 实例文件夹如下：
```
|-sass
    |-css
        |-news
            |-news.scss
        |-product
            |-product.scss

|-static
    |-css
```
```
注：sudo sass --watch时 -> static/css下的目录会自动生成
```

# 命令行编译配置选项.
```
概述：命令行编译sass有配置选项，如编译过后css排版、生成调试map、开启debug信息等，可通过使用命令sass -v查看详细。我们一般常用两种--style``--sourcemap。
```

## 编译格式
```
sass --watch input.scss:output.css --style compact
```

## 编译添加调试map
```
sass --watch input.scss:output.css --sourcemap
```

## 选择编译格式并添加调试map
```
sass --watch input.scss:output.css --style expanded --sourcemap
```

## 开启debug信息
```
sass --watch input.scss:output.css --debug-info
```

```
--style表示解析后的css是什么排版格式.
sass内置有四种编译格式:nested``expanded``compact``compressed.
--sourcemap表示开启sourcemap调试。开启sourcemap调试后，会生成一个后缀名为.css.map文件.
```

# 四种编译排版演示.
未编译样式
```css
.box {
    width: 300px;
    height: 400px;
    &-title {
        height: 30px;
        line-height: 30px;
    }
}
```

# nested编译排版格式.
命令行内容
```
sass style.scss:style.css --style nested
```
 
编译过后样式
```css
.box {
    width: 300px;
    height: 400px; }
.box-title {
    height: 30px;
    line-height: 30px; }
```

# expanded编译排版格式.
命令行内容
```
sass style.scss:style.css --style expanded
```

编译过后样式
```css
.box {
    width: 300px;
    height: 400px;
}
.box-title {
    height: 30px;
    line-height: 30px;
}
```

# compact编译排版格式.
命令行内容
```
sass style.scss:style.css --style compact
```
 
编译过后样式
```css
.box { width: 300px; height: 400px; }
.box-title { height: 30px; line-height: 30px; }
```

# compressed编译排版格式(压缩).
命令行内容
```
sass style.scss:style.css --style compressed
```
 
编译过后样式
```css
.box{width:300px;height:400px}.box-title{height:30px;line-height:30px}
```

# 项目结构.
```
|-sass
    |-main.scss             // 全局样式.
    |-_reboot.scss          // 重置浏览器默认样式.
    |-components            // 【组件】
        |-_components.scss  // 组合所有组件的核心文件.
        |-_alert.scss       // 提示框组件.
        |-_dialog.scss      // 弹出窗口组件.
    |-mixins                // 【混合器】
        |-_mixins.scss      // 组合所有混合气的核心文件.
        |-_box-shadow.scss  // 阴影混合器.
        |-_box-sizing.scss  // 盒模型混合器.
    |-functions             // 【自定义函数】
        |-_functions.scss   // 组合所有自定义函数的核心文件.
        |-_global.scss      // 全局自定义函数.
    |-variables             // 【变量】
        |-_variables.scss   // 全局变量定义.
    |-themes                // 【主题】
        |-_default.scss     // 默认主题.
    |-modules               // 具体模块.
        |-_core.scss        // 模块核心(import变量、混合器、自定义函数……).
        |-domain            // 【域名模块】
            |-domain.scss   // 域名模块

|-css
    |-main.css              // sass生成.
    |-bootstrap.min.css     // 第三方css框架.
    |-modules               // 模块.
        |-domain
            |-domain.css
    |-vendor                // 第三方插件.
        |-date
            |-date.css
```
