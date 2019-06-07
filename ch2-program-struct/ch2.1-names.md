## 2.1 命名

Dart语言的标识符命名规则和C/C++等传统语言类似：以英文字母或美元符号$开头，后面以零个或多个英文字母、美元符号$或数字0-9字符结尾，并区分大小写字母。需要特别注意的是，Dart语言的标识符名称不得有非ASCII字母。

### 2.1.1 强关键字

Dart语言有33个内置的关键字，这些关键字作为保留单词不得用于符命名的名字。内置关键字如下：

```dart
const var final
void enum class extends super this
true false null

if else for in do while
switch case default
try catch throw rethrow finally
return break continue

assert is new
```

<!--
todo: is
-->

其中const表示定义常量，var表示定义变量，final表示定义不可修改的只读量。void表示空类型，enum表示枚举类型，class定义一个类，extends表示类的继承，super表示父类对象，this则表示当前对象。而true、false和null分别是内置的常量值。

if/else/for/in/do/while表示基础的分支和循环控制流语句，switch、case和default对应多分支控制流语句。try/catch/throw/rethrow/finally表示和异常处理相关的语句。return用于函数返回，break和continue分别用于从for和switch等控制流结构中跳出或继续。

assert用于断言，new用于创建对象。需要注意的是，为了配合Flutter平台，在Dart2语言中new和const等将作为可选的关键字使用。

### 2.1.2 弱关键字

除了不能用于标识符名字的内置关键字外，Dart语言还定义了20个内置的弱关键字：

```dart
abstract as covariant deferred
dynamic export external factory
Function get implements import
interface library mixin operator
part set static typedef
```

这类弱关键字和关键字行为很像，但是不是普通的关键字，这类弱关键字不能用于基本的控制流语句。因为除了不能用于类或类型的名字和不能用于导入前缀外，它们可以用于大部分的标识符命名。

比如：

```dart
void main(List<String> args) {
	var abstract = 1;
	print(abstract);
}
```

但是如果将它们用于类的名字，将出现错误：

```dart
class abstract {}
```

错误的提示为“Error: Can't use 'abstract' as a name here.”。


### 2.1.3 上下文关键字


Dart语言还定义了一些上下文关键字：

```dart
show hide
async sync
on
```

<!--
todo: on
-->

比如show和hide用于导入包时精细控制每个标识符的导入方式。async和sync用于和异步、同步编程相关的环境。

在不影响上下文语法的地方，上下文关键字可以用于标识符名字。比如：

```dart
void main(List<String> args) {
	var show = 1;
	var hide = 2;
	var async = 3;
	var sync = 4;
	var on = 5;

	print(show);
	print(hide);
	print(async);
	print(sync);
	print(on);
}
```

运行如下：

```
$ dart hello.dart
1
2
3
4
5
```

这类关键字不仅仅用可以用于定义标识符的名字，还可以用于类的名字：

```dart
class sync {}
```

虽然上下文关键字可以用于标识符名字，但是一般尽量避免这样使用，除非确实可以让程序含义更加明确。

