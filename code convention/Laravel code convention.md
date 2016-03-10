代码风格指导
============

> translate from [PSR-2](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md) 

* [1. 概述]()
    * [1.1 基本规则]()
    * [1.2 例子]()
* [2. 通用规则]()
    * [2.1 基本编码标准]()
    * [2.2 文件]()
    * [2.3 行]()
    * [2.4 缩进]()
    * [2.5 关键字和True/False/Null]()
* [3. 命名空间和Use声明]()
* [4. 类，属性和方法]()
    * [4.1 继承和实现(extends implements)]()
    * [4.2 属性]()
    * [4.3 方法]()
    * [4.4 方法参数]()
    * [4.5 abstract，final，static]()
    * [4.6 方法和函数的调用]()
* [5. 控制结构]()
    * [5.1 if，elseif，else]()
    * [5.2 switch，case]()
    * [5.3 while]()
    * [5.4 for]()
    * [5.5 foreach]()
    * [5.6 try，catch]()
* [6. 闭包(Closure)]()
* [7. 总结]()

**Laravel遵从PSR-2的代码标准以及PSR-4的autoloading标准。**           
    
PSR-2代码风格指导继承并扩展了[PSR-1](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md)的基础的编码标准。      
本指导的主要目的是减少在扫描不同作者的代码时遇到的认知摩擦(congnitive friction)。这主要是通过枚举一套规则，以及规定如何格式化PHP代码来实现的。     
   
这些规则都是根据不同的子项目中的共性推导出来的。当出现多个coder在不同的项目中合作的情况时，这些规则保证在不同项目中使用同一套代码指导方针。因此，这些原则的益处不在于原则本身，而在于原则的分享。    

## 1. 概述
### 1.1 基本规则
* 代码**MUST**遵循代码风格指南[PSR-1](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md).
* 代码**MUST**使用四个空格缩进，不可使用tab。
* 代码行**MUST NOT**严格的长度限制(a hard limit)；基本限制(a soft limit)**MUST**120个字符，行长度应该是80个字符或者更少。
* `namespace`声明后**MUST**有一个空行，在`use`块之后必须有个空行。
* 类声明的左大括号**MUST**单独占一行，右大括号**MUST**在类体后单独占一行。
* 方法的左大括号**MUST**单独占一行，右大括号**MUST**在类体后单独占一行。
* 所有的属性和方法都**MUST**定义可见性(`public, protected, private`)，`abstract` `final`**MUST**定义在可见性之前，而`static`**MUST**定义在可见性之后。
* 控制结构的关键字后**MUST**有一个空格。方法和函数调用则**MUST NOT**。
* 控制结构的左大括号**MUST**在同一行，右大括号**MUST**在结构体的下一行。
* 控制结构的左括号后**MUST NOT**有空格，有括号前**MUST NOT**有空格。     

### 1.2 例子

```php
    <?php
    namespace Vendor\Package;
    
    use FooInterface;
    use BarClass as Bar;
    use OtherVendor\OtherPackage\BazClass;
    
    class Foo extends Bar implements FooInterface
    {
        public function sampleFunction($a, $b = null)
        {
            if ($a === $b) {
                bar();
            } elseif ($a > $b) {
                $foo->bar($arg1);
            } else {
                BazClass::bar($arg2, $arg3);
            }
        }
    
        final public static function bar()
        {
            // method body
        }
    }
```

## 2. 通用规则
### 2.1 基本编码标准
代码**MUST**遵循[PSR-1](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md)的所有规则。

### 2.2 文件
所有`PHP`文件，都**MUST**使用Unix LF(linefeed)在行尾。     
所有的文件最后都**MUST**有一个空行。      
结束标记`?>`在纯php文件中，**MUST**被省略。

### 2.3 行
**MUST NOT**设置行长度的严格限制。     
行长度的软限制**MUST**是120个字符，自动格式检查工具**MUST** 发出警告，但是**MUST NOT**生成错误。     
行长度**SHOULD NOT**超过80个字符；超过这个限制的行**SHOULD**分为多个子行，每一行不可以超过80个字符。    
在非空白行的可见字符之后，**MUST NOT**跟空格。     
**MAY**添加空行来增加代码可读性以及指明相关代码块。     
每一行**MUST NOT**有多条语句。   


### 2.4 缩进
代码**MUST**使用四个空格缩进，不可使用tab。

> 只使用空格，而不是把空格转化为tab，可以避免`diff`, `patch`, `history`, `annotation`等引发的问题。使用空格也可以使在行内对齐(inter-line alignment)时插入细粒度的子缩进更容易(fine-grained sub-indentation)。

### 2.5 关键字和True/False/Null
`PHP`[关键字](http://php.net/manual/en/reserved.keywords.php)**MUST**是小写。   
`PHP`常量`true`, `false`, `null`**MUST**是小写。

## 3. 命名空间和Use声明
当有命名空间时，命名空间后**MUST**有一个空行。   
当存在`use`语句时，所有`use`语句**MUST**在`namespace`之后。    
每个`use`声明，**MUST**有一个`use`关键字。    
每个`use`声明**MUST**占单独一行。   

```php
    <?php
    namespace Vendor\Package;
    
    use FooClass;
    use BarClass as Bar;
    use OtherVendor\OtherPackage\BazClass;
    
    // ... additional PHP code ...
```


## 4. 类，属性和方法
类包含所有的类，接口和trait等。

### 4.1 继承和实现(extends implements)
关键字`extends``implements`必须跟类名在同一行。    
类的左右大括号都**MUST**分别占一行。     

```php
    <?php
    namespace Vendor\Package;
    
    use FooClass;
    use BarClass as Bar;
    use OtherVendor\OtherPackage\BazClass;
    
    class ClassName extends ParentClass implements \ArrayAccess,    \Countable
    {
        // constants, properties, methods
    }
```

`implements`接口的列表可以在多行显示，每一行都缩进一次。当这样处理时，列表中的第一个元素**MUST**换行，每一个接口**MUST**单独占一行。   

```php
    <?php
    namespace Vendor\Package;
    
    use FooClass;
    use BarClass as Bar;
    use OtherVendor\OtherPackage\BazClass;
    
    class ClassName extends ParentClass implements
        \ArrayAccess,
        \Countable,
        \Serializable
    {
        // constants, properties, methods
    }
```

### 4.2 属性
所有的属性**MUST**定义可见性。   
关键字`var`**MUST NOT**被用来声明一个属性。   
一个语句中，**MUST NOT**不能声明超过一个属性。     
属性名**SHOULD NOT**添加单个的下划线前缀来定义`protected`或者`private`可见性。     

```php
    <?php
    namespace Vendor\Package;
    
    class ClassName
    {
        public $foo = null;
    }
```   

### 4.3 方法
所有方法**MUST**声明可见性。     
方法名**SHOULD NOT**添加单个的下划线前缀来定义`protected`或者`private`可见性。     
方法名后**MUST NOT**添加空格。左右大括号都**MUST**单独占一行。在左括号后**MUST NOT**有空格，在右括号前**MUST NOT**有空格。   
    
方法代码块如下。请注意括号，逗号，空格以及花括号的位置。
```php
    <?php
    namespace Vendor\Package;
    
    class ClassName
    {
        public function fooBarBaz($arg1, &$arg2, $arg3 = [])
        {
            // method body
        }
    }
```
### 4.4 方法参数
在方法参数列表中，逗号前**MUST NOT**有任何空格，逗号后**MUST**有一个空格。    
有默认值的参数**MUST**在列表的后面。   

```php
    <?php
    namespace Vendor\Package;
    
    class ClassName
    {
        public function foo($arg1, &$arg2, $arg3 = [])
        {
            // method body
        }
    }
```

方法参数列表**MAY**被分为多行，每一行都缩进一次。如果这样设置的话，第一个**MUST**必须换行，一个参数**MUST**占一行。    
当参数列表分行时，有括号和左大括号**MUST**在单独一行，之间**MUST**有个空格。
```php
    <?php
    namespace Vendor\Package;
    
    class ClassName
    {
        public function aVeryLongMethodName(
            ClassTypeHint $arg1,
            &$arg2,
            array $arg3 = []
        ) {
            // method body
        }
    }
```
### 4.5 abstract，final，static
如果存在，`abstract` `final` **MUST**在可见性之前声明，而`static`**MUST**在可见性之后声明。    

```php
    <?php
    namespace Vendor\Package;
    
    abstract class ClassName
    {
        protected static $foo;
    
        abstract protected function zim();
    
        final public static function bar()
        {
            // method body
        }
    }
```


### 4.6 方法和函数的调用
当调用方法时，方法名和左括号之间**MUST NOT**有空格，左括号之后**MUST NOT**有空格，右括号之前**MUST NOT**有空格。     
在参数列表中，逗号之前**MUST NOT**有空格，逗号之后**MUST**有空格。    

```php
    <?php
    bar();
    $foo->bar($arg1);
    Foo::bar($arg2, $arg3);
```

方法参数列表**MAY**被分为多行，每一行都缩进一次。如果这样设置的话，第一个**MUST**必须换行，一个参数**MUST**占一行。    


```php
    <?php
    $foo->bar(
        $longArgument,
        $longerArgument,
        $muchLongerArgument
    );
```

## 5. 控制结构
控制结构的通用规则如下：
* 在控制结构关键字后**MUST**有一个空格。
* 在左括号后，**MUST NOT**有任何空格。
* 在右括号前，**MUST NOT**有任何空格。
* 在右括号和左大括号之间必须有个空格。
* 控制体必须缩进一次。
* 右大括号必须换行。


### 5.1 if，elseif，else
`if`结构代码块如下。请注意括号，空格以及花括号的位置；`else`和`elseif`跟前一段代码的右大括号在同一行。

```php
    <?php
    if ($expr1) {
        // if body
    } elseif ($expr2) {
        // elseif body
    } else {
        // else body;
    }
```

### 5.2 switch，case
`switch`代码块如下。请注意括号，空格以及花括号的位置。`case`**MUST**相对于`switch`缩进一级，`break`关键字(或者其他关键字)**MUST**具有`case`代码块同样的缩进。在非空的故意不break的`case`代码块后，**MUST**有一个明显的注释：`// no break`。

```php
    <?php
    switch ($expr) {
        case 0:
            echo 'First case, with a break';
            break;
        case 1:
            echo 'Second case, which falls through';
            // no break
        case 2:
        case 3:
        case 4:
            echo 'Third case, return instead of break';
            return;
        default:
            echo 'Default case';
            break;
    }
```

### 5.3 while
`while`代码块如下。请注意括号，空格以及花括号的位置。

```php
    <?php
    while ($expr) {
        // structure body
    }
```

同样，`do while`代码块如下。请注意括号，空格以及花括号的位置。

```php
    <?php
    do {
        // structure body;
    } while ($expr);
```


### 5.4 for
`for`代码块如下。请注意括号，空格以及花括号的位置。

```php
    <?php
    for ($i = 0; $i < 10; $i++) {
        // for body
    }
```

### 5.5 foreach
`foreach`代码块如下。请注意括号，空格以及花括号的位置。

```php
    <?php
    foreach ($iterable as $key => $ value) { 
        // foreach body
    }
```

### 5.6 try，catch
`try catch`代码块如下。请注意括号，空格以及花括号的位置。  

```php
    <?php
    try {
        // try body
    } catch (FirstExceptionType $e) {
        // catch body
    } catch (OtherExceptionType $e) {
        // catch body
    }

```

## 6. 闭包(Closure)


## 7. 总结
本原则有意忽略了一些风格和实践的元素，包括单不限于：    
* 全局变量和全局常量的声明。
* 声明函数
* 操作符和赋值
* 行间对齐
* 注释和文档块(document blocks)
* 类名的前缀和后缀
* 最佳实践



