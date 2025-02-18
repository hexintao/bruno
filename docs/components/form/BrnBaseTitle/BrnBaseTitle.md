---
title: BrnBaseTitle
group:
  title: Form
  order: 12
---

# BrnBaseTitle

可组合基础标题类型表单。

## 一、效果总览

![](./img/BrnBaseTitleIntro.png)

## 二、描述

### 适用场景

右侧可传入自定义widget

### 交互规则

1. 设置此录入项是否可编辑（禁用）。
2. 包括"标题"、"副标题"、"错误信息提示"、"必填项提示"、"添加/删除按钮"、"消息提示"、"多选项"等元素。
3. 右侧自定义区域时图限制最大高度 25。
4. 标题、副标题视图均支持自定义视图。

### 注意事项

该组件不具备数据录入的功能，可以用来和其他表单项做拼装，以实现更复杂的功能。

## 三、构造函数及参数说明

### 构造函数


```dart
BrnBaseTitle({
    Key key,
    this.title: "",
    this.subTitle,
    this.isRequire: false,
    this.isEdit: true,
    this.error: "",
    this.tipLabel,
    this.titleWidget,
    this.subTitleWidget,
    this.customActionWidget,
    this.onTip,
    this.themeData,
  }) {
    this.themeData ??= BrnFormItemConfig();
    this.themeData = BrnThemeConfigurator.instance
        .getConfig(configId: this.themeData.configId)
        .formItemConfig
        .merge(this.themeData);
  }
```
### 参数说明

| **参数名** | **参数类型** | **描述** | **是否必填** | **默认值** | **备注** |
| --- | --- | --- | --- | --- | --- |
| title | String | 录入项标题 | 否 | '' |  |
| titleWidget | Widget | 录入项标题Widget | 否 | 无 |  |
| subTitle | String | 录入项子标题 | 否 | 无 |  |
| subTitleWidget | Widget | 录入项子标题Widget | 否 | 无 |  |
| tipLabel | String | 录入项提示（问号图标&文案） 用户点击时触发onTip回调。 | 否 | 备注中类型3 | 1. 设置"空字符串"时展示问号图标 2. 设置"非空字符串"时展示问号图标&文案 3. 若不赋值或赋值为null时，不显示提示项 |
| error | String | 录入项错误提示 | 否 | '' |  |
| isRequire | bool | 录入项是否为必填项（展示`*`图标） 默认为 false 不必填 | 否 | false |  |
| isEdit | bool | 录入项 是否可编辑 | 否 | true | true：可编辑，false：禁用 |
| customActionWidget | Widget | 自定义Widget | 否 | 无 |  |
| onTip | VoidCallback | 点击"？"图标回调 | 否 | 无 | 见**tipLabel**字段 |
| themeData | BrnFormItemConfig | 表单主题配置 | 否 | 无 | |


## 四、代码演示

### 效果1：基本样式

![](./img/BrnBaseTitleDemo1.png)
```dart
BrnBaseTitle(
  title: "基本样式",
  subTitle: "这里是副标题",
  onTip: () {
    BrnToast.show("点击触发回调_onTip", context);
  },
),
```
### 效果2：全功能样式，自定义右侧视图

![](./img/BrnBaseTitleDemo2.png)
```dart
BrnBaseTitle(
  error: "必填项不能为空",
  title: "全功能样式",
  subTitle: "这里是副标题",
  tipLabel: "提示",
  isRequire: true,
  customActionWidget: Container(
    color:Colors.lightBlue,
    child: Center(
      child: Text('我是自定义视图', style: TextStyle(color: Colors.white))
    ),
  ),
  onTip: () {
    BrnToast.show("点击触发回调_onTip", context);
  },
),
```
