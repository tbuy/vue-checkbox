# 组件

>


## 安装

```
npm install
```

## 运行

```
npm run dev
```

## api

名称 | 类型 | 默认值 | 是否必选 | 描述
---|--- |--- |--- | ---
questionNo | Array | [1,2,3] | no | 问题序号显示形式（如1，2，3; I, II, III）
answerNo | Array | [] | yes | 选项序号显示形式（如A, B, C; I, II, III）
question | Array | [] | yes | 问题及选项内容 [{title: 题目, type: 单选或者多选, options: 选项}]
