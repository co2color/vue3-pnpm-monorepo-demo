# vue3-pnpm-monorepo-demo

该项目总共有三个子项目，如果你只想快速体验，那么依次运行：
`npm i -g pnpm`
`pnpm i -w`
然后，三个子项目分别运行
`pnpm project1`
`pnpm project2`
`pnpm project3`


## 开始
###### 
###### 如果你没有装pnpm，请先`npm i -g pnpm`  (node.js version>14.9+)

###### 然后根目录`pnpm i -w`（win下pnpm可能需要在git bash/cmd环境使用，powershell可能会error。另，pnpm初次i可能比较慢，但>1次后很快）

###### 运行某项目：`pnpm xxx`，如运行packages下的project1项目： `pnpm project1`


#### 新建项目流程(以新建项目projectA为例)：
在packages文件夹下创建项目文件夹如projectA；cd projectA，然后npm init，得以创建package.json文件；改成如下内容：
```json
{
  "name": "@project/projectA",
  "version": "0.0.0",
  "private": true,
  "scripts": {
    "dev": "vite --host",
    "build": "vite build",
    "serve": "vite preview",
    "lint": "eslint --ext .js,.ts,.vue src/"
  }
}
```
##### 
如果有projectA项目特定的（仅projectA需要，其他项目不需要）包，则在根目录下用该命令：
```dotnetcli
pnpm i xxx -r --filter @project/projectA
```
切记，@project/projectA这个字段必须和projectA/paclage.json的name一致。

如需安装全局包（放在根目录package.json下，所有项目皆可使用）：
```dotnetcli
pnpm i xx -w
```

(使用 -w 表示把包安装在 root 下，该包会放置在 `root/node_modules` 下。而如若要把包安装在某个项目中，则使用 -r 代替 -w。必须使用其中一个参数。）

运行和打包该项目：在根目录package.json script下添加：`"projectA": "pnpm run -C packages/projectA dev"`和`"build:projectA": "pnpm run -C packages/projectA build"`。然后`pnpm projectA`即可运行。

#### 新建全局工具库/函数/资源方法：
比如，你想在根目录创建别的工具文件夹如全局公共assets资源文件夹用来存放全部项目的公共图片资源，则：
* 根目录创建assets；
* `cd assets`，在assets下npm init，初始一个package.json，将name改为@xx/assets；
* pnpm-workspace.yaml新增一行`  - 'assets/**'`
* 根package.json的workspaces加上assets；
* `cd ../`，在根目录`pnpm i @xx/assets -w`；
至此，根package.json dependencies会多一个 "@xx/assets": "workspace:^x.x.x"，搞定~

###### pnpm官网：https://pnpm.io/

###### pnpm+monorepo简介：

* https://juejin.cn/post/6964328103447363614
* https://juejin.cn/post/7077168840806760478