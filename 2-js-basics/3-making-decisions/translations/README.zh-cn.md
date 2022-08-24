# JavaScript 基础：做出决定

![JavaScript Basics - Making decisions](/sketchnotes/webdev101-js-decisions.png)
> 涂鸦笔记作者：[Tomomi Imura](https://twitter.com/girlie_mac)

## 课前小测
[课前小测](https://ff-quizzes.netlify.app/quiz/11?loc=zh_cn)

对你的代码运行方式做出决定并且控制它们的顺序可以让你的代码更加可复用和稳定。这节课会介绍 JavaScript 中控制数据流的语法以及其与布尔数据类型搭配使用时的重要性。

[![Making Decisions](https://img.youtube.com/vi/SxTp8j-fMMY/0.jpg)](https://youtube.com/watch?v=SxTp8j-fMMY "做出决定")

> 点击上方图片来观看一个有关做出决定的视频。

## 布尔值简要回顾

布尔值只有两个值：`true` 或 `false`。布尔值有助于决定在满足一定条件下应该运行哪些行的代码。

可以用如下方式将你的布尔变量设为真或假：

`let myTrueBool = true`
`let myFalseBool = false`

✅ 布尔值（Booleans）的命名来源于英国数学家、哲学家和逻辑学家 George Boole（1815-1864）。

## 比较运算符（Comparison Operators）与布尔值

一些运算符可用于表示比较的结果（会以布尔值返回）。下面是一些常用的运算符：

| 符号  | 描述                                                                              | 示例               |
| ----- | --------------------------------------------------------------------------------- | ------------------ |
| `<`   | **小于**：比较两个值，如果左边的值小于右边的值则返回 `true`                       | `5 < 6 // true`    |
| `<=`  | **小于或等于**：比较两个值，如果左边的值小于或等于右边的值则返回 `true`           | `5 <= 6 // true`   |
| `>`   | **大于**：比较两个值，如果左边的值大于右边的值则返回 `true`                       | `5 > 6 // false`   |
| `>=`  | **大于或等于**：比较两个值，如果左边的值大于或等于右边的值则返回 `true`           | `5 >= 6 // false`  |
| `===` | **严格等于**：比较两个值，如果左边的值等于右边的值**且**数据类型相同则返回 `true` | `5 === 6 // false` |
| `!==` | **不等于**：比较两个值，返回与“严格等于”运算结果相反的布尔值                      | `5 !== 6 // true`  |

✅ 在你的浏览器控制台中亲手写一些比较来验证你的知识。有任何让你感到意外的返回结果吗？

## If 语句

If 语句会在条件为真的情况下运行它的块中的代码。

```javascript
if (condition){
    // 如果 condition 为 true，这个块中的代码将会运行。
}
```

比较/逻辑运算符常被用于构造条件式。

```javascript
let currentMoney;
let laptopPrice;

if (currentMoney >= laptopPrice){
    // 如果条件为 true，这个块中的代码将会运行。
    console.log("Getting a new laptop!");
}
```

## If..Else 语句

`else` 语句会在条件为假的情况下运行它块中的代码。它后面可以跟上一个 `if` 语句。

```javascript
let currentMoney;
let laptopPrice;

if (currentMoney >= laptopPrice){
    // 如果条件为 true，这个块中的代码将会运行。
    console.log("Getting a new laptop!");
}
else{
    // 如果条件为 false，这个块中的代码将会运行。
    console.log("Can't afford a new laptop, yet!");
}
```

✅ 通过在浏览器控制台运行上方和接下来的代码来检查你对它的理解是否正确。可以通过修改 currentMoney 和 laptopPrice 变量的值来尝试改变 `console.log()` 打印出的值。

## 逻辑运算符（Logical Operators）与布尔值

做出决定可能需要不止一次比较，可以用逻辑运算符将比较结果串在一起来产生一个布尔值。

| 符号   | 描述                                                                | 示例                                                   |
| ------ | ------------------------------------------------------------------- | ------------------------------------------------------ |
| `&&`   | **逻辑与（AND）**：比较两个布尔表达式，只有在两边**都是真**时返回真 | `(5 > 6) && (5 < 6 ) // 一边为假，另一边为真，返回假`  |
| `\|\|` | **逻辑或（OR）**：比较两个布尔表达式，在至少一边为真时返回真        | `(5 > 6) \|\| (5 < 6) // 一边为假，另一边为真，返回真` |
| `!`    | **逻辑非（NOT）**：返回与一个布尔表达式相反的布尔值                 | `!(5 > 6) // 5 并不比 6 大，但 "!" 会返回真`           |

## 用逻辑运算符来构造条件和决定

If...else 语句中，逻辑运算符可以用来构造条件。

```javascript
let currentMoney;
let laptopPrice;
let laptopDiscountPrice = laptopPrice - (laptopPrice * .20) // 打八折后的笔记本电脑价格

if (currentMoney >= laptopPrice || currentMoney >= laptopDiscountPrice){
    // 如果条件为 true，这个块中的代码将会运行。
    console.log("Getting a new laptop!");
}
else {
    // 如果条件为 false，这个块中的代码将会运行。
    console.log("Can't afford a new laptop, yet!");
}
```

### 取反运算符（Negation operator）

你现在已经了解到如何用 `if...else` 语句来创建条件逻辑。任何传入 `if` 的东西都需要计算出一个 true 或者 false。通过 `!` 运算符你可以将表达式 _取反_。就像这样：

```javascript
if (!condition) {
  // 如果 condition 为 false 则运行
} else {
  // 如果 condition 为 true 则运行
}
```

### 三元表达式（Ternary expressions）

`if...else` 并非表达决定逻辑的唯一方式，你也可以使用一个叫做三元运算符的东西。语法如下：

```javascript
let variable = condition ? <若为 true 则返回这个> : <若为 false 则返回这个>
```

下方是一个更具体的例子：

```javascript
let firstNumber = 20;
let secondNumber = 10
let biggestNumber = firstNumber > secondNumber ? firstNumber: secondNumber;
```

✅ 花一分钟多看几遍上方代码，你能想明白这些运算符是什么意思吗？

上方代码表示：

- 如果 `firstNumber` 大于 `secondNumber`
- 就将 `firstNumber` 赋值给 `biggestNumber`
- 否则将 `secondNumber` 赋值给 `biggestNumber`

三元表达式其实只是下方代码的一个简单写法：

```javascript
let biggestNumber;
if (firstNumber > secondNumber) {
  biggestNumber = firstNumber;
} else {
  biggestNumber = secondNumber;
}
```

---

## 🚀 挑战

用逻辑运算符写一个程序，然后用三元表达式重写它。你更喜欢哪种语法？

---
## 课后小测
[Post-lecture quiz](https://ff-quizzes.netlify.app/quiz/12?loc=zh_cn)

## 复习 & 自学

在 [MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators) 上了解更多开发者可以使用的运算符。

试用一下由 Josh Comeau 制作的绝妙的[运算符查询器](https://joshwcomeau.com/operator-lookup/)！

## 作业

[运算符](assignment.zh-cn.md)
