# imooc-admin

## Project setup

```
yarn install
```

### Compiles and hot-reloads for development

```
yarn serve
```

### Compiles and minifies for production

```
yarn build
```

### Lints and fixes files

```
yarn lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

###

新增 commitlint 记录规范分支
1.commitlint: 用于检查提交信息
2.husky: 是`git hook`工具

//一。commitlint 1.安装依赖
npm install --save-dev @commitlint/config-conventional@12.1.4 @commitlint/cli@12.1.4

2.创建 commitlint.config.js 文件夹

echo "module.exports = {extends: ['@commitlint/config-conventional']}" >
commitlint.config.js

3.打开 commitlint.config.js ，增加配置项目（config-conventional 默认配置点击可查看);
module.exports = {
//继承的规则
extends: ['@commitlint/config-conventional'],
//定义规则
roles: {
//type 的类型定义： 表示 git 提交的 type 必须再以下类型范围之内
'type-enum': [
//当前验证的错误级别
2,
//在什么情况下进行验证
'always',
//泛型内容
[
'feat', //新功能
'fix', //修复 bug
'docs', //文档注释
'refactor', //重构
'perf', //性能优化
'test', //增加测试
'chore', //构建过程或辅助工具的变动
'revert',//回退
'build' //打包
],
],
// subject 大小写不做交易
'subject-case':[0]
}
}

//二。 husky

1. 安装依赖
   npm install husky@7.0.1 --save-dev

2. 启动 hooks，生成.husky 文件夹
   npx husky install

3. 在 package.json 中生成 prepare 指令 （需要 npm 7.x 以上版本）
   npm set-script prepare "husky install"

4. 执行 prepare 指令
   npm run prepare

5. 执行成功，提升

6. 添加 commitlint 的 hook 到 husky 中，并指令在 commit-msg 的 hooks 下执行 npx --no-install commitlint --edit "$1"指令

npx husky add .husky/commit-msg 'npx --no-install commitlint --edit "$1"'

7.此时的.husky 的文件结构

至此不符合规范的 commit 讲不再可提交
