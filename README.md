# 组件

> 基于vue简单的选项组件，使用于单选或者多选答题类型的表单。答题数据需要根据api结构传递给组件，选项结果回通过question中selected属性返回给用户。

## 安装

```
npm install
```

## 运行

```
npm run dev
```

## 构建

```
npm run-script build
```

## 查看demo

```
node ./app.js
```

[运行app.js后点击查看demo](http://localhost:3000/#/)


## api

名称 | 类型 | 默认值 | 是否必选 | 描述
---|--- |--- |--- | ---
questionNo | Array | [1,2,3] | false | 问题序号显示形式（如1，2，3; I, II, III）
answerNo | Array | [] | true | 选项序号显示形式（如A, B, C; I, II, III）
question | Array | [] | true | 问题及选项内容

> question:[{title: 题目, type: 单选或者多选, options: 选项, selected: 选择结果}]
