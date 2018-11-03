##### 命令

```
地址：https://stencil.bigcommerce.com/docs/stencil-cli-options
stencil init:创建 .stencil 文件
stencil start
	-e : 跑本地版本
	-n:无缓存
	--theme-editor-port 9000：修改端口
    -v MyCustomVariation ：测试不同的变种
stencil bundle:打包成.zip，最大50MB
stencil push:将.zip发布到商店

卸载stencil
	npm uninstall -g @bigcommerce/stencil-cli

```

##### 主题目录结构

```
templates/pages:页面模板，页面名称不可以改动
	引用layout下的模板: {{> /layout/base}}
templates/components： snippets  和 partials 等自定义代码
	components可以调用components
templates/layout：定义网站结构，可以有多个
assets ：images CSS and JavaScript files
lang ：en.json这个是必须的
```

##### 对象参照

```
https://stencil.bigcommerce.com/docs/stencil-object-model
```

##### config.json各参数含义

```
https://stencil.bigcommerce.com/docs/configjson-reference
作用：
	定义全局变量
	主题的变种版本（1-4个）
	变种版本变量
```

##### schema.json的含义

```
https://stencil.bigcommerce.com/docs/schemajson-metadata-for-theme-editor
```

##### 获取config.json值

```
在scss中
$color-highlight:       stencilColor("color-highlight");
```

##### ZURB响应式框架

```
https://foundation.zurb.com/sites/docs/v/5.5.3/
```

##### scss规范

```
https://github.com/bigcommerce/sass-style-guide
```

##### 事件钩子

```

```

##### handlebars中的helper

```
参考：https://stencil.bigcommerce.com/docs/handlebars-helpers-reference
地址：https://stencil.bigcommerce.com/docs/other-handlebars-helpers#cdn
使用cdn引用图片：
	<img src="{{cdn "webdav:img/image.jpg"}}">
向JS注入配置文件中的变量：
	{{inject 'productThumbSize' theme_settings.productthumb_size}}
```

##### Front-matter

```
#用来定义申明数据
#缩进只能用空格，不能用tab
#不能超过64kb
属性定义：https://stencil.bigcommerce.com/docs/front-matter-variables
---
products:
    new:
    	limit: {{theme_settings.homepage_new_products_count}}
---
只能在<theme-name>/templates/pages/ 目录下使用
不能使用的目录：
	<theme-name>/templates/components/
	<theme-name>/templates/layout/
	<theme-name>/templates/pages/custom/
```

