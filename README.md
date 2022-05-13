# umi框架搭建

最近好忙啊，去隔壁部门帮忙了，一拖再拖导致我们部门的项目也进行不了，哎。

回归正题—————-

本次要新建一个基于react的`umi + typescript + dva + antd` 的框架（要求umi2.0，antd3.0）

因为ts、dva、antd都可以在umi创建过程中进行配置，所以重点只在于安装和配置umi框架。

<br />

## 环境要求

node ≥ 8.10 ，可以通过 `node -v` 进行查看

<br />

## 安装步骤
1. 全局安装umi
安装umi，指定版本为2.9.0，版本可自己选择，在2.0.0以上就可以

```jsx
yarn global add umi@2.9.0 
```

> FAQ：安装完成后，用 `umi -v` 查看版本，如果提示 **umi: command not found，**你需要将 `yarn global bin` 路径配置到环境变量中，方法如下：
> 

```jsx
# mac 系统:
$ sudo vi ~/.bash_profile
# 在 .bash_profile 中添加下面一行：
export PATH="$PATH:`yarn global bin`"

# windows系统:
# 获取 global bin 的路径
$ yarn global bin
C:UsersAdministratorAppDataLocalYarnbin
# 复制上面的 global bin 的路径，添加到系统环境变量 PATH。
```

2. 创建umi项目
新建目录进入，执行下面命令

```jsx
yarn create umi
```

```markdown
按照提示选择：
选择创建类型    app
是否使用TypeScript？   y
选择多个模块（空格选择，上下键移动）
（*）dva
（*）antd
创建完毕————
```
<br />


## 完善项目

1. 目录完善

刚建好的umi项目是不完整的，需要按照约定在/src增加如下目录

![image](https://user-images.githubusercontent.com/70362312/168264994-4837672a-d2c8-453f-bac3-c290ab810f95.png)

2. `.umirc.ts`文件

theme：制定主题

disableCSSModules：禁用css module

alias：设置之后，文件引用可以通过 “@/src/”方式进行

proxy：设置接口访问的基地址


```jsx
theme: './src/utils/theme.js',
disableCSSModules: true,
alias: {
  api: resolve(__dirname, './src/services/'),
  components: resolve(__dirname, './src/components'),
  containers: resolve(__dirname, './src/containers'),
  models: resolve(__dirname, './src/models'),
  services: resolve(__dirname, './src/services'),
  utils: resolve(__dirname, './src/utils'),
  assets: resolve(__dirname, './src/assets'),
},
proxy: {
  '/api': {
    target: 'http://192.168.190.157:24680/',
    changeOrigin: true,
    pathRewrite: { '^/api': '/' },
  },
},
env: {
  development: {
    extraBabelPlugins: ['dva-hmr'],
  },
},
```

3. layouts设置

    待写...

4. 下载依赖 `yarn `
