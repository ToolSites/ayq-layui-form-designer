# ayq-layui-form-designer

#### 介绍
基于layui的表单设计器,前期设计基于fwr-layui-formdesigner，因fwr-layui-formdesigner存在很多问题，不在维护，即基于这个上重新做了开发

#### 声明：基本代码已经上传，可以在上面玩一玩，测试一下BUG，希望大家提出问题，也希望大家参与进来，提供一些有趣的组件，现在发布第一版本V1.0.0，开发和编写文档不易，要求不多，给个Star支持一下，需要一些开发动力，嘿嘿

#### 演示地址
[http://www.ayq.com/](http://116.62.237.101:8009/)

#### 说明：基本组件已经写得差不多，后面会优化整体的功能，提升体验感，后续会优化一些显示特效，主要会做表单数据的获取与回显，手写签名组件暂时不开源，手写签名自适应pc和移动端，但可以体验一些，提出有用的意见。

#### 手写签名演示地址
[http://www.ayqsign.com/](http://116.62.237.101:8009/HandwrittenSignature/index.html)

#### 使用说明

1. 本项目基于Layui、Jquery、Sortable
2. 项目已经基本实现了拖动布局，父子布局
3. 项目实现了大部分基于Layui的Form表单控件布局，包括输入框、编辑器、下拉、单选、单选组、多选组、日期、滑块、评分、轮播、图片、颜色选择、图片上传、文件上传、日期范围、排序文本框、图标选择器、cron表达式、手写签名组件

#### 开发计划

1.  支持layui表单组件
2.  支持layui的扩展组件
3.  支持通过formDesigner对象的方法获取填写表单的数据或者回显表单数据
4.  支持代码自动生成
5.  支持通过url获取远程数据动态显示组件（如下拉框、编辑器、图片等）
6.  支持定制布局和背景

![输入图片说明](https://images.gitee.com/uploads/images/2021/0524/161635_1627108b_4776207.png "13.PNG")
![输入图片说明](https://images.gitee.com/uploads/images/2021/0527/094341_983939d5_4776207.png "14.PNG")

#### 入门案例（设计页面）


```
var render = formDesigner.render({
                data:[],//表单设计数据
                elem:'#formdesigner'
            });

//重新渲染数据
render.reload(options)

//获取相关配置信息
render.getOptions() 

//获取表单设计数据
render.getData()
//获取外部编辑器对象
render.geticeEditorObjects()
```

#### 入门案例（视图页面）


```
var render = formPreview.render({
          elem: '#testdemo',
          data: [],//表单设计数据
          formData: {"textarea_1":"123",
            "input_2":"123",
            "password_3":"123"}//要回显的表单数据
        });
//重新渲染数据
render.reload(options)

//获取相关配置信息
render.getOptions() 

//获取表单设计数据
render.getData()

//获取外部编辑器对象
render.geticeEditorObjects()

//获取上传图片的id与上传路径
render.getImages()
//数据案例 select 对应文件对象的id uploadUrl对应文件的上传路径
[{select: "imageimage_2",uploadUrl: ""}]

//获取上传文件的id与上传路径
render.getFiles()
//数据案例 select 对应文件对象的id uploadUrl对应文件的上传路径
[{select: ""filefile_1"",uploadUrl: ""}]

//获取表单数据 
**
注意: 当前方法会避开校验规则，最好放在表单提交里面 
form.on('submit(demo1)', function(data){}）；
** 
render.getFormData()

//回显表单数据 
render.setFormData(json)

//全局禁用表单
render.globalDisable()

//全局启用表单
render.globalNoDisable()

 ** 
说明：  这些方法有2个组件不受控制（文件组件和图片组件），
我把这两个组件通过方法单独提出来，因为文件上传的方式比较多，
提出来让使用者自己去定义和实现自己的文件上传方式，
具体的案例在preview.html里面已经写好，你们自己参考
** 
```

#### 基础参数

| 参数  | 类型  | 说明  |  示例值 |
|---|---|---|---|
|  elem |  String | 指定原始 table 容器的选择器，方法渲染方式必填  | "#elem"  |
|  data |  Array | 直接赋值数据  |  [{},{},...] |
|  formData|  Array | 回显的表单数据  |  [{},{},...] |

#### 组件参数

| 参数  | 类型  | 说明  |  示例值 |
|---|---|---|---|
|  id |  String | 指定组件标识（唯一），表单提交字段name值  | "field"  |
|  label | String  | 文本框标题  |  "姓名" |
|  tag | String  | 表单类型  |  "input" |
|  placeholder | String  | placeholder  |  "请输入" |
|  defaultValue | object  | 组件默认值  |  "姓名" |
|  width | String  | 组件宽度  |  "100%" |
|  labelWidth | String  | 文本框宽度  |  "250px" |
|  readonly | Boolean  | 只读  |  true,false |
|  disabled | Boolean  | 禁用  |  true,false |
|  required | Boolean  | 必填  |  true,false |
|  columns | number  | 栅格布局列数  |  true,false |
|  maxValue | object  | 最大值  |  "" |
|  minValue | object  | 最小值  |  "" |
|  expression | String  | 验证  |  "email" |
|  stepValue | number  | 滑块步长  |  2 |
|  isInput | Boolean  | 滑块显示输入框  |  true,false |
|  datetype | String  | 日期类型  |  "时间选择器" |
|  dateformat | String  | 日期格式  |  "yyyy-MM-dd" |
|  rateLength | number  | 星星个数  |  5 |
|  interval | number  | 轮播间隔毫秒  |  3000 |
|  autoplay | Boolean  | 轮播自动切换  |  true,false |
|  anim | object  | 切换方式  |  {text: '左右切换', value: 'default'} |
|  arrow | object  | 切换箭头  |  {text: '悬停显示', value: 'hover'} |

#### 更新日志
- 2021-06-15 
    1. 增加输入框layui提供的基本校验规则
    2. 禁用的显示效果优化
    3. 优化表单展示滑块、评分、颜色选择器提交无法获取字段值得问题
- 2021-06-17 
    1. 增加时间范围组件（暂未提交代码）
    2. 页面自适应优化
- 2021-06-22 
    1. 增加时间范围组件
    2. 展示页面提交参数优化
- 2021-06-24 
    1. 引入iceEditor富文本编辑组件
- 2021-06-30 
    1. 加入iceEditor富文本编辑组件
    2. 解决一行多列样式异常问题
    3. 结局一行多列嵌套问题
    4. 优化富文本参数无法获取问题
- 2021-07-01 
    1. 加入排序文本框组件
    2. 加入图标选择器组件
    3. 加入Cron表达式组件
    4. 优化富文本编辑器（菜单编辑本地直接访问会出现跨域问题，放入nginx、tomcat等容器就会正常）
    5. 发布V1.0.0
- 2021-07-23 
    1. 更新版本V1.0.1
    2. 加入标签组件
    3. 加入按钮组件
    4. 优化栅栏格内部拖动是出现样式混乱问题
    5. 优化已放入多个的组件，拖动排序无效问题
    6. 优化标签组件标签过多，组件排序样式出现错位问题
- 2021-08-03 
    1. 加入手写签名组件
- 2021-08-11 
    1. 优化各个组件间的交互
    2. 表单视图新增表单数据的获取与回显
    3. 表单视图新增禁用表单与启用表单
    4. 更新版本V1.1.0
- 2021-08-26 
    1. 下拉，多选，单选，轮播配置多个选项增加拖拽功能
    2. 优化下拉，多选，单选，轮播默认选项（配置和设计页面都可以设置默认值）
    3. 优化宽度体验，改成滑块
    4. 增加修改文本框长度属性,滑块操作
    5. 增加必填项展示加*
    6. 优化生成代码功能
    7. 增加新建窗口中打开展示页面
    8. 更新版本V1.1.5

#### 特技

1.  使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2.  Gitee 官方博客 [blog.gitee.com](https://blog.gitee.com)
3.  你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解 Gitee 上的优秀开源项目
4.  [GVP](https://gitee.com/gvp) 全称是 Gitee 最有价值开源项目，是综合评定出的优秀开源项目
5.  Gitee 官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6.  Gitee 封面人物是一档用来展示 Gitee 会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)
