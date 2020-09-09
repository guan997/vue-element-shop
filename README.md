### 安装依赖

```
npm install
```

### 导入数据库
### 初始化后台文件
node .\app.js
error: -4078 数据库没有连接成功，调试数据库之后再连接

### 开启后台接口 
node .\app.js

### 本地运行：

**npm run serve** 运行之后，会默认打开本地访问路径：[http://localhost:8080](http://localhost:8080)

#### 发布：

**npm run bulid** (生成打包之后的项目文件,此文件主要用于项目部署)。

---



### ESlint报错：

Trailing spaces not allowed no-trailing-spaces
解决方案：
1.某行代码后面存在空格,去掉空格
2.调整规则,设定允许空格和空行
项目.eslintrc.js文件 rules节点下设定

```
rules: {
    'no-console': process.env.NODE_ENV === 'production' ? 'warn' : 'off',
    'no-debugger': process.env.NODE_ENV === 'production' ? 'warn' : 'off',
    'no-trailing-spaces':["error", { "ignoreComments": true ,"skipBlankLines":true}]
    // ignoreComments 允许注释尾随空格,skipBlankLines允许 空行空格
  }
```


### 登录/退出功能
1. 编写登录页面

2. 实现表单验证
2.1 使用Form 组件，为el-form通过 rules 属性绑定约定的验证规则对象
2.2 定义验证规则属性
2.3 将 Form-Item 的 prop 属性设置为需校验的字段名

3. 实现重置功能
3.1 通过ref 获取表单实例对象
3.2 调用resetFields()方法对整个表单进行重置 (数据恢复成默认值，因为其是双向数据绑定)

4. 实现登录校验功能
4.1 通过ref 获取表单实例对象
4.2 调用validate()方法	对整个表单进行校验的方法参数为一个回调函数。
4.3 实现登录结果信息提示
4.4 将登录成功之后的 token，保存到客户端的 sessionStorage 中
4.5 通过编程式导航跳转到后台主页，路由地址是 /home

5. 实现登录功能
5.1 通过路由导航守卫控制访问权限

6. 实现退出功能

处理ESlint语法报错
添加格式化配置文件，   
 // 使用分号, 默认true
    "semi": false,
 // 使用单引号, 默认false(在jsx中配置无效, 默认都是双引号)
    "singleQuote": false,
//  每行超过200强制换行
      "printWidth":200
```
{
  "semi": false,
  "singleQuote": true,
  "printWidth":200
}  
```

函数名称或function关键字与开始参数之间允许有空格
.eslintrc.js
```
  rules: {
    'space-before-function-paren': 0
  },
```


### 主页布局
1. 页面效果实现
2. 左侧菜单栏数据获取
3. 通过双层for循环渲染左侧菜单
- ndex只接受字符串,不接受数值,在后面拼接字符串
4. 为选中项设置颜色并添加分类图标
5. 实现侧边栏的折叠与展开效果

### 实现用户页面布局

### 实现用户页面的功能

### 未解决bug(已解决)

进入页面后出现MessageBox弹框
Vue element-ui引入MessageBox导致每个页面刷新后均弹出空的提示消息
解决办法：
将Vue.use(Message)改为Vue.component(Message.name, Message)即可

### 实现权限列表布局

### 实现权限列表功能

### 实现角色列表页面

### 实现角色列表功能（编辑和删除同角色列表以及添加角色功能 已完成）

解决分配角色defKeys数组不断变多的问题

### 实现用户界面分配角色功能

### 实现商品分类布局

安装vue-table-with-tree-grid插件 展示数据

### 实现商品分类数据展示功能

### 实现添加商品分类

使用级联选择器

### 完善角色列表功能

发现bug（Element插件问题）
修改角色名称时，角色名称会出现第一次赋值的结果，一闪而过

发现bug（已解决）
当数据超过一定量的时候，级联选择器的显示范围为当前可视页面的全部，而且超过当前可视页面
在globel全局样式文件中加入此代码
.el-cascader-menu{height:240px}

### 完成商品分类主功能（删除和编辑功能暂未完成  => 已完成）

### 实现分类参数所有功能

注意：显示过的数据应清空，防止无数据项时出现上次显示的数据

### 实现商品列表主要功能

get请求需要使用{params：value}
this.$http.delete(`goods/${id}`)

### 实现商品列表中的添加商品功能(完成)

1.添加步骤条和tab栏
2.使用上传组件 上传图片
注意：上传组件没有指定axios，需要指定headers
3.使用富文本vue-quill-editor 添加商品内容
4.对goods_cat使用lodash进行深拷贝后再进行验证数据信息
5.对attrs数组进行数据处理

出现bug (已解决)
Cannot read property 'forEach' of undefined
原因：monyTableDate表单数据获取失败 
解决方案：monyTableDate => manyTableDate

### 实现订单列表功能

1.实现布局
2.获取订单数据
3.使用TimeLine组件实现物流信息时间线显示

### 实现数据报表界面
使用Echarts渲染数据

### 项目优化和上线
- 通过nprogress添加进度条效果
- 解决serve命令中提示的ESLint语法错误
- 在执行build命令期间移除所有的console
- 只在发布阶段移除所有的console
- 修改默认打包入口文件
 -  webpack配置关闭 webpack 的性能提示
- 通过externals加载外部CDN资源
- 通过CDN优化ElementUI的打包
- 实现路由懒加载
- 开启文件的Gzip网络传输压缩文件体积
- 配置HTTPS服务
- 使用pm2管理应用
