
# 特约

想要贡献`react-values`?那将是真棒!

-   [报告错误](#reporting-bugs)
-   [提交拉请求](#submitting-pull-requests)
-   [运行示例](#running-examples)
-   [运行测试](#running-tests)
-   [发布版本](#publishing-releases)

## 报告错误

如果您在使用库时遇到任何奇怪的行为,请随意在此存储库中打开新问题!请跑一个**开放前搜索**一个新问题,以确保其他人尚未报告或解决您找到的错误. 

## 提交拉请求

所有拉动请求都非常欢迎,非常感谢!请详细说明pull请求引入或更改的新逻辑,以及测试和文档!

## 运行示例

您可以在本地运行示例: 

    yarn install
    yarn start

这将打开示例`http://localhost:8888`你来参观当您进行任何更改时,它们将重新加载. 

## 运行测试

要运行测试,您需要将存储库克隆到您的计算机. 在那之后,你需要`cd`进入克隆它的目录,并安装依赖项`yarn`并运行测试: 

    yarn install
    yarn test

如果您需要调试某些内容,可以添加一个`debugger`行到源,然后运行`yarn test debug`. 

## 发布版本

要发布库运行的新版本: 

```js
yarn release
```

然后按照提示进行操作[`np`](https://github.com/sindresorhus/np)给你. 如果有任何重大更改,请务必选择正确的升级类型!
