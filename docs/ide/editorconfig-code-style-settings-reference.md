---
title: "Параметры соглашений о написании кода .NET в EditorConfig | Документация Майкрософт"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 1
author: kaseyu
ms.author: kaseyu
manager: davidcsa
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 3037d92e9de377ab4b306a5a0e164e29fa6659e7
ms.openlocfilehash: 600cd62e7843274b52da5ac7200b5168311cab07
ms.contentlocale: ru-ru
ms.lasthandoff: 08/07/2017

---

# <a name="net-coding-convention-settings-for-editorconfig"></a>Параметры соглашений о написании кода .NET в EditorConfig
Соглашения о написании кода .NET настраиваются в файле [EditorConfig](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options). Файлы EditorConfig позволяют **включить или отключить отдельные соглашения о написании кода .NET** и **настроить строгость применения этих соглашений** (уровень серьезности). Дополнительные сведения об использовании EditorConfig для обеспечения согласованности базы кода см. [в этой статье](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options).

В .NET поддерживаются следующие три категории соглашений о написании кода.
- **[Языковые соглашения](#language)** — правила, относящиеся к языку C# или Visual Basic, например использование элементов, воплощающих выражение, с типом `var`/explicit.
- **[Правила форматирования](#formatting)** — правила, описывающие макет и структуру кода для повышения его читаемости, например стиль скобок Олмана или пробелы в блоках управления.
- **[Соглашения об именовании](#naming)** определяют правила именования объектов: например, все методы `async` должны оканчиваться на Async. 

# <a name="language">Языковые соглашения</a>
## <a name="overview"></a>Обзор
**Формат правила:**
`options_name = false|true : none|suggestion|warning|error`

Для параметра стиля кода необходимо указать **true** (предпочитать этот параметр) или **false** (не предпочитать этот параметр), двоеточие (`:`) и уровень серьезности (`none`, `silent`, `suggestion`, `warning` или `error`). Серьезность означает требуемый уровень выполнения для этого стиля в базе данных кода.

`none` и `silent` являются синонимами. Они обозначают, что для пользователя не будут отображаться никакие сообщения. По сути это означает отключение правила.

Серьезность | effect
------------ | -------------
none/silent | Ничего не показывать пользователю, если этот стиль не соблюдается, однако функции создания кода будут в нем работать. 
suggestion | Если этот стиль не соблюдается, показывать его пользователю как предложение (базовые точки в первых двух символах).
предупреждение | Если этот стиль не соблюдается, выводить предупреждение компилятора.
error | Если этот стиль не соблюдается, выводить ошибку компилятора.

## <a name="net-language-convention-options"></a>Параметры языковых соглашений для .NET

- **[Параметры стиля кода .NET](#this_and_me)**
    - [Квалификация "This." и "Me."](#this_and_me)
        - [Поля](#this_and_me_fields)
        - [Свойства](#this_and_me_properties)
        - [Методы](#this_and_me_methods)
        - [События](#this_and_me_events)
    - [Ключевые слова языка (int, string и т. д.) и имена типов .NET Framework для ссылок на типы](#language_keywords)
        - [Локальные переменные, параметры и элементы](#language_keywords_variables)
        - [Выражения доступа к элементам](#language_keywords_member_access)
    - [Настройки уровня выражений](#expression_level)
        - [Инициализаторы объектов](#expression_level_object_initializers)
        - [Инициализаторы коллекций](#expression_level_collection_initializers)
        - [Явные имена кортежей](#expression_level_tuple_names)
        - [Выражения объединения в проверке "null"](#expression_level_null_checking)
        - [Распространение значений NULL в проверке "null"](#expression_level_null_propogation)
- **[Параметры стиля кода C#](#csharp_codestyle)**
    - ["var"](#var)
        - ["var" для встроенных типов](#var_built_in)
        - ["var", если тип является очевидным](#var_apparent)
        - ["var" в другом месте](#var_elsewhere)
    - [Элементы, воплощающие выражение](#expression_body)
        - [Методы](#expression_bodied_members_methods)
        - [Конструкторы](#expression_bodied_members_constructors)
        - [Операторы](#expression_bodied_members_operators)
        - [Свойства](#expression_bodied_members_properties)
        - [Индексаторы](#expression_bodied_members_indexers)
        - [Методы доступа](#expression_bodied_members_accessors)
    - [Сопоставление шаблонов](#pattern_matching)
        - ["is" с проверкой "cast"](#pattern_matching_is_cast)
        - ["as"с проверкой "null"](#pattern_matching_as_null)
    - [Встроенные объявления переменных](#inlined_variable_declarations)
    - [Настройки уровня выражения](#expression_level_csharp)-[Упрощение выражений `default`](#expression_level_default)
    - [Параметры проверки "null"](#null_checking)
        - [Выражения throw](#null_checking_throw_expressions)
        - [Вызовы условного делегата](#null_checking_conditional_delegate_calls)

## <a name="this_and_me">Квалификация "This." и "Me."</a>
### <a name="this_and_me_fields">Поля (IDE0003/IDE0009)</a>
|  Имя параметра | `dotnet_style_qualification_for_field` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать, чтобы все нестатические поля, используемые в нестатических методах, предварялись `this.` в C# или `Me.` в Visual Basic. | **C#:** <br>`this.capacity = 0;` <br><br> **Visual Basic:** <br> `Me.capacity = 0`
| False | Предпочитать, чтобы все нестатические поля, используемые в нестатических методах, не предварялись `this.` в C# или `Me.` в Visual Basic. | **C#:** <br>`capacity = 0;` <br><br> **Visual Basic:** <br>`capacity = 0`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_field = false:suggestion
```

### <a name="this_and_me_properties">Свойства (IDE0003/IDE0009)</a>

|  Имя параметра | `dotnet_style_qualification_for_property` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать, чтобы все нестатические свойства, используемые в нестатических методах, предварялись `this.` в C# или `Me.` в Visual Basic.| **C#:** <br>`this.ID = 0;` <br><br> **Visual Basic:** <br>`Me.ID = 0`
| False | Предпочитать, чтобы все нестатические свойства, используемые в нестатических методах, *не* предварялись `this.` в C# или `Me.` в Visual Basic. | **C#:** <br>`ID = 0;` <br><br> **Visual Basic:** <br> `ID = 0`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_property = false:suggestion
```

### <a name="this_and_me_methods">Методы (IDE0003/IDE0009)</a>
|  Имя параметра | `dotnet_style_qualification_for_method` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать, чтобы все нестатические методы, вызываемые из нестатических методов, предварялись `this.` в C# или `Me.` в Visual Basic.| **C#:** <br>`this.Display();` <br><br> **Visual Basic:** <br> `Me.Display()`
| False | Предпочитать, чтобы все нестатические методы, вызываемые из нестатических методов, *не* предварялись `this.` в C# или `Me.` в Visual Basic. | **C#:** <br>`Display();` <br><br> **Visual Basic:** <br> `Display()`


#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_method = false:suggestion
```

### <a name="this_and_me_events">События (IDE0003/IDE0009)</a>
|  Имя параметра | `dotnet_style_qualification_for_event` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать, чтобы все нестатические события, на которые существуют ссылки в нестатических методах, предварялись `this.` в C# или `Me.` в Visual Basic.| **C#:** <br>`this.Elapsed += Handler;` <br><br> **Visual Basic:** <br> `AddHandler Me.Elapsed, AddressOf Handler`
| False | Предпочитать, чтобы все нестатические события, на которые существуют ссылки в нестатических методах, *не* предварялись `this.` в C# или `Me.` в Visual Basic. | **C#:** <br>`Elapsed += Handler;` <br><br> **Visual Basic:** <br>`AddHandler Elapsed, AddressOf Handler`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_event = false:suggestion
```

## <a name="language_keywords">Ключевые слова языка (int, string и т. д.) и имена типов .NET Framework для ссылок на типы</a>
### <a name="language_keywords_variables"> Локальные переменные, параметры и элементы (IDE0012/IDE0014)</a>
|  Имя параметра | `dotnet_style_predefined_type_for_locals_parameters_members` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Для локальных переменных, параметров и элементов типов предпочитать, чтобы типы с представляющим их ключевым словом языка (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) использовали ключевое слово вместо имени типа (`Int32`, `Int64` и т. д.).| **C#:** <br>`private int _member;` <br><br> **Visual Basic:** `Private _member As Integer`
| False | Для локальных переменных, параметров и элементов типов предпочитать, чтобы типы с представляющим их ключевым словом языка (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) использовали имя типа (`Int32`, `Int64` и т. д.) вместо ключевого слова.  | **C#:** <br>`private Int32 _member;` <br><br> **Visual Basic:** <br> `Private _member As Int32`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
``` 

### <a name="language_keywords_member_access">Выражения доступа к элементу (IDE0013/IDE0015)</a>
|  Имя параметра | `dotnet_style_predefined_type_for_member_access` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать ключевое слово при использовании выражения доступа к элементам в типе, представленном ключевым словом (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`).| **C#:** <br>`var local = int.MaxValue;` <br><br> **Visual Basic:** <br> `Dim local = Integer.MaxValue`
| False | Предпочитать имя типа при использовании выражения доступа к элементам в типе, представленном ключевым словом (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`). | **C#:** <br>`var local = Int32.MaxValue;` <br><br> **Visual Basic:** <br> `Dim local = Int32.MaxValue`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

## <a name="expression_level">Настройки уровня выражений</a>
### <a name="expression_level_object_initializers">Инициализаторы объектов (IDE0017)</a>
|  Имя параметра | `dotnet_style_object_initializer` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать инициализировать объекты с помощью инициализаторов объектов, когда это возможно.| **C#:** <br>`var c = new Customer(){ Age = 21 };` <br><br> **Visual Basic:** <br> `Dim c = New Customer() With { .Age = 21 }`
| False | Предпочитать *не* инициализировать объекты с помощью инициализаторов объектов. | **C#:** <br>`var c = new Customer();`<br>`c.Age = 21;` <br><br> **Visual Basic:** <br>`Dim c = new Customer() `<br>`c.Age = 21`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_object_initializer = true:suggestion
``` 

### <a name="expression_level_collection_initializers">Инициализаторы коллекций (IDE0028)</a>
|  Имя параметра | `dotnet_style_collection_initializer` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать инициализировать коллекции с помощью инициализаторов коллекций, когда это возможно.| **C#:** <br>`var list = new List<int>{ 1, 2, 3 };` <br><br> **Visual Basic:** <br> `Dim list = new List(Of Integer) From { 1, 2, 3}`
| False | Предпочитать *не* инициализировать коллекции с помощью инициализаторов коллекций. | **C#:** <br>`var list = new List<int>();`<br>`list.Add(1);`<br>`list.Add(2);`<br>`list.Add(3);` <br><br> **Visual Basic:** <br>`Dim list = new List(Of Integer)`<br>`list.Add(1)`<br>`list.Add(2)`<br>`list.Add(3)`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_collection_initializer = true:suggestion
```

### <a name="expression_level_tuple_names">Явные имена кортежей (IDE0033)</a>
|  Имя параметра | `dotnet_style_explicit_tuple_names` |
| ------------- |:-------------:|
| **Применимые языки** | C# 7.0+ и Visual Basic 15+

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать имена кортежей свойствам ItemX.| **C#:** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.name;` <br><br> **Visual Basic:** <br> `Dim customer As (name As String, age As Integer) = GetCustomer()`<br>`Dim name = customer.name`
| False | Предпочитать свойства ItemX именам кортежей. | **C#:** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.Item1;` <br><br> **Visual Basic:** <br>`Dim customer As (name As String, age As Integer) = GetCustomer()`<br> `Dim name = customer.Item1`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_explicit_tuple_names = true:suggestion
``` 

### <a name="expression_level_null_checking">Объединение выражений при проверке NULL (IDE0029)</a>
|  Имя параметра | `dotnet_style_coalesce_expression` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать выражение объединения со значением NULL проверке тернарного оператора.| **C#:** <br>`var v = x ?? y;` <br><br> **Visual Basic:** <br> `Dim v = If(x, y)`
| False | Предпочитать проверку тернарного оператора выражению объединения со значением NULL. | **C#:** <br>`var v = x != null ? x : y; // or`<br>`var v = x == null ? y : x;` <br><br> **Visual Basic:** <br>`Dim v = If(x Is Nothing, y, x) ' or`<br> `Dim v = If(x IsNot Nothing, x, y)`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_coalesce_expression = true:suggestion
``` 

### <a name="expression_level_null_propogation">Распространение значений NULL при проверке NULL (IDE0031)</a>
|  Имя параметра | `dotnet_style_null_propagation` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать использовать условный оператор со значением NULL, где это возможно.| **C#:** <br>`var v = o?.ToString();` <br><br> **Visual Basic:** <br> `Dim v = o?.ToString()`
| False | Предпочитать использовать тернарную проверку "null", где это возможно. | **C#:** <br>`var v = o == null ? null : o.ToString(); // or`<br>`var v = o != null ? o.String() : null;` <br><br> **Visual Basic:** <br>`Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or`<br> `Dim v = If(o IsNot Nothing, o.ToString(), Nothing)`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_null_propagation = true:suggestion
``` 

# <a name="csharp_codestyle">Параметры стиля кода C#</a>
## <a name="var">var и явные типы</a>
### <a name="var_built_in">var для встроенных типов (IDE0007, IDE0008)</a>
|  Имя параметра | `csharp_style_var_for_built_in_types` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать, чтобы `var` использовался для встроенных системных типов, таких как `int`.| **C#:** <br>`var x = 5;`
| False | Предпочитать, чтобы `var` не использовался для встроенных системных типов, таких как `int`. | **C#:** <br>`int x = 5;`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
``` 

### <a name="var_apparent">var для очевидных типов (IDE0007, IDE0008)</a>
|  Имя параметра | `csharp_style_var_when_type_is_apparent` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать использовать `var`, если тип уже упоминается в правой части выражения объявления.| **C#:** <br>`var obj = new C();`
| False | Предпочитать не использовать `var`, если тип уже упоминается в правой части выражения объявления. | **C#:** <br>`C obj = new C();`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_var_when_type_is_apparent = true:suggestion
``` 

### <a name="var_elsewhere">var в других ситуациях (IDE0007, IDE0008)</a>
|  Имя параметра | `csharp_style_var_elsewhere` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать `var` во всех случаях, если не переопределено другим правилом стиля кода.| **C#:** <br>`var f = this.Init();`
| False | Предпочитать не использовать var во всех случаях, если не переопределено другим правилом стиля кода.| **C#:** <br>`bool f = this.Init();`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_var_elsewhere = true:suggestion
``` 

##<a name="expression_bodied_members">Элементы, воплощающие выражение</a>
### <a name="expression_bodied_members_methods">Методы (IDE0022)</a>
|  Имя параметра | `csharp_style_expression_bodied_methods` |
| ------------- |:-------------:|
| **Применимые языки** | C# 6.0+

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать элементы, воплощающие выражение, для методов.| **C#:** <br>`public int GetAge() => this.Age;`
| False | Не предпочитать элементы, воплощающие выражение, для методов.| **C#:** <br>`public int GetAge() { return this.Age; }`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
``` 

### <a name="expression_bodied_members_constructors">Конструкторы (IDE0021)</a>
|  Имя параметра | `csharp_style_expression_bodied_constructors` |
| ------------- |:-------------:|
| **Применимые языки** | C# 6.0+

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать элементы, воплощающие выражение, для конструкторов.| **C#:** <br>`public Customer(int age) => Age = age;`
| False | Не предпочитать элементы, воплощающие выражение, для конструкторов.| **C#:** <br>`public Customer(int age) { Age = age; }`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_constructors = false:none
``` 

### <a name="expression_bodied_members_operators">Операторы (IDE0023, IDE0024)</a>
|  Имя параметра | `csharp_style_expression_bodied_operators` |
| ------------- |:-------------:|
| **Применимые языки** | C# 6.0+

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать элементы, воплощающие выражение, для операторов.| **C#:** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`=> new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);`
| False | Не предпочитать элементы, воплощающие выражение, для операторов.| **C#:** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_operators = false:none
``` 

### <a name="expression_bodied_members_properties">Свойства (IDE0025)</a>
|  Имя параметра | `csharp_style_expression_bodied_properties` |
| ------------- |:-------------:|
| **Применимые языки** | C# 7.0+

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать элементы, воплощающие выражение, для свойств.| **C#:** <br>`public int Age => _age;`
| False | Не предпочитать элементы, воплощающие выражение, для свойств.| **C#:** <br>`public int Age { get { return _age; }}`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_properties = false:none
``` 

### <a name="expression_bodied_members_indexers">Индексаторы (IDE0026)</a>
|  Имя параметра | `csharp_style_expression_bodied_indexers` |
| ------------- |:-------------:|
| **Применимые языки** | C# 7.0+

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать элементы, воплощающие выражение, для индексаторов.| **C#:** <br>`public T this[int i] => _value[i];`
| False | Не предпочитать элементы, воплощающие выражение, для индексаторов.| **C#:** <br>`public T this[int i] { get { return _values[i]; } }`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_indexers = false:none
``` 

### <a name="expression_bodied_members_accessors">Методы доступа (IDE0027)</a>
|  Имя параметра | `csharp_style_expression_bodied_accessors` |
| ------------- |:-------------:|
| **Применимые языки** | C# 7.0+

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать элементы, воплощающие выражение, для методов доступа.| **C#:** <br>`public int Age { get => _age; set => _age = value; }`
| False | Не предпочитать элементы, воплощающие выражение, для методов доступа.| **C#:** <br>`public int Age { get { return _age; } set { _age = value; } }`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_accessors = false:none
``` 

## <a name="pattern_matching">Сопоставление шаблонов</a>
### <a name="pattern_matching_is_cast">is с проверкой cast (IDE0020)</a>
|  Имя параметра | `csharp_style_pattern_matching_over_is_with_cast_check` |
| ------------- |:-------------:|
| **Применимые языки** | C# 7.0+

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать сопоставления шаблонов вместо выражений `is` с приведениями типов.| **C#:** <br>`if (o is int i) {...}`
| False | Предпочитать выражения `is` с приведениями типов вместо сопоставления шаблонов.| **C#:** <br>`if (o is int) {var i = (int)o; ... }`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
```

### <a name="pattern_matching_as_null">as с проверкой NULL (IDE0019)</a>
|  Имя параметра | `csharp_style_pattern_matching_over_as_with_null_check` |
| ------------- |:-------------:|
| **Применимые языки** | C# 7.0+

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать сопоставление шаблонов вместо выражений `as` с проверками "null", чтобы определить, имеет ли что-то определенный тип.| **C#:** <br>`if (o is string s) {...}`
| False | Предпочитать выражения `as` с проверками "null" вместо соответствия шаблонам, чтобы определить, имеет ли что-то определенный тип.| **C#:** <br>`var s = o as string; if (s != null) {...}`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

### <a name="inlined_variable_declarations">Встроенные объявления переменных IDE0018)</a>
|  Имя параметра | `csharp_style_inlined_variable_declaration` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать встроенное объявление переменных `out`, когда возможно. | **C#:** <br>`if (int.TryParse(value, out int i) {...}`
| False | Предпочитать явное объявление переменных `out`.| **C#:** <br>`int i; if (int.TryParse(value, out i) {...}`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```
## <a name="expression_level_csharp">Настройки уровня выражений</a>
### <a name="expression_level_default">Упрощение выражений `default` (IDE0034)</a>
|  Имя параметра | `csharp_prefer_simple_default_expression` |
| ------------- |:-------------:|
| **Применимые языки** | C# 7.1+ и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| True | Предпочитать `default` вместо `default(T)` | **C#:** <br>`void DoWork(CancellationToken cancellationToken = default){ ... }`
| False | Предпочитать | **C#:** <br>`void DoWork(CancellationToken cancellationToken = default(CancellationToken)){ ... }`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
``` 

## <a name="null_checking">Параметры проверки "null"</a>
### <a name="null_checking_throw_expressions">Выражения throw (IDE0016)</a>
|  Имя параметра | `csharp_style_throw_expression` |
| ------------- |:-------------:|
| **Применимые языки** | C# 7.0+

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать использовать выражения throw вместо операторов throw. | **C#:** <br>`this.s = ss ?? throw new ArgumentNullException(nameof(s));`
| False | Предпочитать использовать операторы throw вместо выражений throw.| **C#:** <br>`if (s==null) {throw new ArgumentNullException(nameof(s));} this.s = s;`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
```

### <a name="null_checking_conditional_delegate_calls">Предпочитать условные вызовы делегата (IDE0041)</a>
|  Имя параметра | `csharp_style_conditional_delegate_call` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать использовать условную операцию объединения (`?.`) при вызове лямбда-выражения вместо выполнения проверки "null". | **C#:** <br>`func?.Invoke(args);`
| False | Предпочитать выполнять проверку "null" перед вызовом лямбда-выражения вместо использования условного оператора объединения (`?.`).| **C#:** <br>`if (func!=null) { func(args); }`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_conditional_delegate_call = false:suggestion
```

# <a name="formatting"> Правила форматирования</a>
## <a name="overview"></a>Обзор
**Формат правила:**
`options_name = false|true`

В параметрах форматирования используются значения **true** (предпочитать этот параметр) или **false** (не предпочитать этот параметр), за несколькими исключениями, для которых нужно указать, в каких условиях применяется это правило.

## <a name="net-formatting-options"></a>Параметры форматирования .NET

- **[Параметры форматирования .NET](#usings)**
    - [Управление директивами using](#usings)
        - [Помещать системные директивы первыми при сортировке](#usings_sort_system_first)
- **[Параметры форматирования C#](#newline)**
    - [Параметры перевода строки](#newline)
        - [Новая строка перед открывающей скобкой (`{`)](#newline_before_brace)
        - [Новая строка перед `else`](#newline_before_else)
        - [Новая строка перед `catch`](#newline_before_catch)
        - [Новая строка перед `finally`](#newline_before_finally)
        - [Новая строка перед элементами в инициализаторах объектов](#newline_before_object)
        - [Новая строка перед элементами в анонимных типах](#newline_before_anonymous)
        - [Новая строка перед элементами в предложениях выражений запроса](#newline_before_query)
    - [Параметры отступа](#indent)
        - [Отступ в конструкции `switch` case](#indent_switch)
        - [Размещение меток](#label)
    - [Параметры интервалов](#spacing)
        - [Пробел после приведения](#space_after_cast)
        - [Пробел после ключевых слов в операторах потока управления](#space_control_flow)
        - [Пробел между скобками в списке параметров при объявлении метода](#space_parameter_list)
        - [Пробел между скобками в списке аргументов при вызове метода](#space_method_call)
        - [Пробел между скобками в других ситуациях](#space_other)
    - [Параметры переноса](#wrapping)
        - [Оставлять выражения и объявления элемента в одной строке](#wrapping_statement)
        - [Оставлять блок в одной строке](#wrapping_block)

## <a name="usings">Управление директивами using</a>
### <a name="usings_sort_system_first">Помещать системные директивы первыми при сортировке</a>
|  Имя параметра | `dotnet_sort_system_directives_first` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| True | Сортировать директивы using System.* в алфавитном порядке, располагая их перед всеми остальными директивами using.| **C#:** <br>`using System.Collections.Generic;`<br> `using System.Threading.Tasks;`<br> `using Octokit;`
| False | Никаких ограничений на сортировку директив using | **C#:** <br>`using System.Collections.Generic;`<br> `using Octokit;` <br> `using System.Threading.Tasks;`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# .NET formatting settings:
[*.cs, *.vb]
dotnet_sort_system_directives_first = true
``` 

# <a name="csharp_formatting">Параметры форматирования C#</a>
## <a name="newline">Параметры перевода строки</a>
### <a name="newline_before_brace">Новая строка перед открывающей скобкой (`{`)</a>
|  Имя параметра | `csharp_new_line_before_open_brace` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание 
| ------------- |:-------------|
| accessors, anonymous_methods, anonymous_types, control_blocks, events, indexers, lambdas, local_functions, methods, object_collection, properties, types. (Если значений несколько, разделяйте их запятыми). | Требовать, чтобы фигурные скобки для определенных выражений размещались в новой строке (стиль Олмана) |
| все | Требовать, чтобы фигурные скобки для всех выражений размещались в новой строке (стиль Олмана) |
| Нет | Требовать, чтобы фигурные скобки для всех выражений размещались в строке выражения (стиль Кернигана и Ритчи) |

#### <a name="applied"></a>Область применения:
```csharp
// csharp_new_line_before_open_brace = all
void MyMethod() 
{
    if (...) 
    {
        ...
    }
}
```

```csharp
// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
``` 

### <a name="newline_before_else"> Новая строка перед `else`</a>
|  Имя параметра | `csharp_new_line_before_else` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание 
| ------------- |:-------------|
| True | Размещать инструкции `else` в новой строке.  |
| False | Размещать инструкции `else` в одной строке.  |

#### <a name="applied"></a>Область применения:
```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}
```

```csharp
// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_else = true
``` 

### <a name="newline_before_catch"> Новая строка перед `catch`</a>
|  Имя параметра | `csharp_new_line_before_catch` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание 
| ------------- |:-------------|
| True | Размещать инструкции `catch` в новой строке.  |
| False | Размещать инструкции `catch` в одной строке. |

#### <a name="applied"></a>Область применения:
```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}
```

```csharp
// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_catch = true
``` 

### <a name="newline_before_finally"> Новая строка перед `finally`</a>
|  Имя параметра | `csharp_new_line_before_catch` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание 
| ------------- |:-------------|
| True | Требовать, чтобы инструкции `finally` размещались в новой строке после закрывающей фигурной скобки.  |
| False | Требовать, чтобы инструкции `finally` размещались в одной строке после закрывающей фигурной скобки.  |

#### <a name="applied"></a>Область применения:
```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}
```

```csharp
// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_finally = true
``` 

### <a name="newline_before_object"> Новая строка перед элементами в инициализаторах объектов</a>
|  Имя параметра | `csharp_new_line_before_members_in_object_initializers` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание 
| ------------- |:-------------|
| True | Требовать, чтобы элементы инициализаторов объектов размещались в разных строках.  |
| False | Требовать, чтобы элементы инициализаторов объектов размещались в одной строке.  |

#### <a name="applied"></a>Область применения:
```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}
```

```csharp
// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_members_in_object_initializers = true
``` 

### <a name="newline_before_anonymous"> Новая строка перед элементами в анонимных типах</a>
|  Имя параметра | `csharp_new_line_before_members_in_anonymous_types` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание 
| ------------- |:-------------|
| True | Требовать, чтобы элементы анонимных типов размещались в разных строках.  |
| False | Требовать, чтобы элементы анонимных типов размещались в одной строке.  |

#### <a name="applied"></a>Область применения:
```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}
```

```csharp
// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_members_in_anonymous_types = true
``` 

### <a name="newline_before_query"> Новая строка перед элементами в предложениях выражений запроса</a>
|  Имя параметра | `csharp_new_line_within_query_expression_clauses` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание 
| ------------- |:-------------|
| True | Требовать, чтобы элементы в предложениях выражений запросов размещались в отдельных строках.  |
| False | Требовать, чтобы элементы в предложениях выражений запросов размещались в одной строке.  |

#### <a name="applied"></a>Область применения:
```csharp
// csharp_new_line_within_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;
```

```csharp
// csharp_new_line_within_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_within_query_expression_clauses = true
``` 

## <a name="indent">Параметры отступа</a>
### <a name="indent_switch">Отступ в конструкции `switch` case</a>
|  Имя параметра | `csharp_indent_case_contents` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание 
| ------------- |:-------------|
| True | Отступ в конструкции `switch` case  |
| False | Нет отступа в конструкции `switch` case |

#### <a name="applied"></a>Область применения:
```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}
```

```csharp
// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
``` 

### <a name="label">Размещение меток</a>
|  Имя параметра | `csharp_indent_labels` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание 
| ------------- |:-------------|
| one_less | Метки размещаются на предыдущей позиции отступа относительно текущего контекста |
| no_change | Метки размещаются на той же позиции отступа, что и текущий контекст |

#### <a name="applied"></a>Область применения:
```csharp
// csharp_indent_labels = one_less
private string MyMethod(...) 
{
    if (...) {
        goto error;
    }
error:
    throw new Exception(...);
}

```

```csharp
// csharp_indent_labels= no_change
private string MyMethod(...) 
{
    if (...) {
        goto error;
    }
    error:
    throw new Exception(...);
}
```

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_indent_labels = one_less
``` 

## <a name="spacing">Параметры интервалов</a>
### <a name="space_after_cast"> Пробел после приведения</a>
|  Имя параметра | `csharp_space_after_cast` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен |
| ------------- |:-------------|:-------------|
| True | Требовать наличие пробела между типом и значением в приведении  | **C#:** <br>`int y = (int) x;`
| False | Требовать отсутствие пробела между типом и значением в приведении | **C#:** <br>`int y = (int)x;`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
``` 

### <a name="space_control_flow"> Пробел после ключевых слов в операторах потока управления</a>
|  Имя параметра | `csharp_space_after_keywords_in_control_flow_statements` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен |
| ------------- |:-------------|:-------------|
| True | Требовать пробел после ключевого слова | **C#:** <br>`for (int i;i<x;i++) { ... }`
| False | Требовать отсутствие пробела после ключевого слова | **C#:** <br>`for(int i;i<x;i++) { ... }`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_space_after_keywords_in_control_flow_statements = true
``` 

### <a name="space_parameter_list"> Пробел между скобками в списке аргументов при объявлении метода</a>
|  Имя параметра | `csharp_space_between_method_declaration_parameter_list_parentheses` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен |
| ------------- |:-------------|:-------------|
| True | Требовать пробел после ключевого слова | **C#:** <br>`void Bark( int x ) { ... }`
| False | Требовать отсутствие пробела после ключевого слова | **C#:** <br>`void Bark(int x) { ... }`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_method_declaration_parameter_list_parentheses = true
```

### <a name="space_method_call"> Пробел между скобками в списке аргументов при вызове метода</a>
|  Имя параметра | `csharp_space_between_method_call_parameter_list_parentheses` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен |
| ------------- |:-------------|:-------------|
| true | Добавлять пробел между скобками для операторов потока управления | **C#:** <br>`MyMethod( argument );`
| false | Добавлять пробел между скобками для выражений | **C#:** <br>`MyMethod(argument);`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_method_call_parameter_list_parentheses = control_flow_statements, type_casts
```  

### <a name="space_other"> Пробел между скобками в других ситуациях</a>
|  Имя параметра | `csharp_space_between_parentheses` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен |
| ------------- |:-------------|:-------------|
| control_flow_statements | Добавлять пробел между скобками для операторов потока управления | **C#:** <br>`for( int i;i<x;i++ ) { ... }`
| выражения | Добавлять пробел между скобками для выражений | **C#:** <br>`var z = ( x * y ) - ( ( y - x ) * 3);`
| type_casts | Размещать пробел между скобками в приведениях типов | **C#:**<br>`int y = ( int )x;`

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_parentheses = control_flow_statements, type_casts
``` 

## <a name="wrapping">Параметры переноса</a>
### <a name="wrapping_statement">Оставлять выражения и объявления элемента в одной строке</a>
|  Имя параметра | `csharp_preserve_single_line_statements` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание |
| ------------- |:-------------|
| True | Оставлять выражения и объявления элемента в одной строке  | 
| False | Оставлять выражения и объявления элемента в разных строках | 

#### <a name="applied"></a>Применен
```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";
```

```csharp
//csharp_preserve_single_line_statements = false
int i = 0; 
string name = "John";
```

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
``` 

### <a name="wrapping_block">Оставлять блок в одной строке</a>
|  Имя параметра | `csharp_preserve_single_line_blocks` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание |
| ------------- |:-------------|
| True | Оставлять блок в одной строке | 
| False | Оставлять блок в разных строках | 

#### <a name="applied"></a>Применен
```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }
```

```csharp
//csharp_preserve_single_line_blocks = false
public int MyProperty
{ 
    get; set;
}
```

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_blocks = true
``` 

# <a name="naming"> Соглашения об именовании</a>
## <a name="overview"></a>Обзор
**Формат правила:**<br>
namingRuleTitle:<br>
`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`<br>
`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`<br>
`dotnet_naming_rule.<namingRuleTitle>.severity = none|suggestion|warning|error`<br>
<br>
symbolTitle:<br>
`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = class, struct, interface, enum, property, method, field, event, namespace, delegate, type_parameter`<br>
`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = public, internal, private, protected, protected_internal`<br>
`dotnet_naming_symbols.<symbolTitle>.required_modifiers = abstract, async, const, readonly, static`<br>
<br>
styleTitle:<br>
`dotnet_naming_style.<styleTitle>.capitalization = pascal_case|camel_case|first_word_upper|all_upper|all_lower`<br>
`dotnet_naming_style.<styleTitle>.required_prefix = string`<br>
`dotnet_naming_style.<styleTitle>.required_suffix = string`<br>
`dotnet_naming_style.<styleTitle>.word_separator = string`<br>

## <a name="writing-a-naming-convention"></a>Создание соглашения об именовании
Для соглашений об именовании нужно указать **символы**, **стиль** и **уровень серьезности**. Соглашения об именовании следует сортировать от наиболее конкретных к наименее конкретным. Применяться будет только первое обнаруженное правило. 

### <a name="severity"></a>Серьезность
Ниже приведены допустимые варианты уровней серьезности для правил стиля именования: `none`, `silent`, `suggestion`, `warning`, `error`.

 `none` и `silent` являются синонимами. Они обозначают, что для пользователя не будут отображаться никакие сообщения. По сути это означает отключение правила.

 `suggestion` означает, что пользователю будут предоставлены следующие сообщения в списке ошибок и в интегрированной среде разработки. Серьезность `suggetion` означает использование правила именования, но не позволяет ему прерывать сборку.

Серьезность | effect
------------ | -------------
none/silent | Ничего не показывать пользователю, если этот стиль не соблюдается, однако функции создания кода будут в нем работать. 
suggestion | Если этот стиль не соблюдается, показывать его пользователю как предложение (базовые точки в первых двух символах).
предупреждение | Если этот стиль не соблюдается, выводить предупреждение компилятора.
error | Если этот стиль не соблюдается, выводить ошибку компилятора.

### <a name="symbol-specification"></a>Спецификации символов
Определяет, к _каким_ символам _с какими_ модификаторами и _на каком_ уровне доступности применяется это правило именования.

|  Имя параметра | `dotnet_naming_rule.<namingRuleTitle>.symbols` |
| ------------- |:-------------:|
|  | `dotnet_naming_symbols.<symbolTitle>.applicable_kinds`
|  | `dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities`
|  | `dotnet_naming_symbols.<symbolTitle>.required_modifiers`

| Символ | Специальные возможности | Модификаторы
| ------------- |------------- |------------- |
| `*` | `*` |  `abstract` | 
| `class` | `public` |  `must_inherit` | `async` | 
| `struct` | `internal` (C#) /  | `const` | 
| `interface` | `friend` (Visual Basic) | `readonly` | 
| `enum` | `private`  | `static` | 
| `property` | `protected` | `shared` |
| `method` |`protected_internal` (C#) | |
| `field` | `protected_friend` (Visual Basic) | |
| `event` | | |
| `delegate` | | |

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp formatting settings:
[*.cs]
dotnet_naming_rule.async_methods_end_in_async.symbols = any_async_methods

dotnet_naming_symbols.any_async_methods.applicable_kinds = method
dotnet_naming_symbols.any_async_methods.applicable_accessibilities = *
dotnet_naming_symbols.any_async_methods.required_modifiers = async
``` 

### <a name="style-specification"></a>Спецификация стиля
Определяет стиль именования, применяемый к символам.

|  Имя параметра | `dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>` |
| ------------- |:-------------:|
|  | `dotnet_naming_style.<styleTitle>.capitalization`|
|  | `dotnet_naming_style.<styleTitle>.required_prefix`|
|  | `dotnet_naming_style.<styleTitle>.required_suffix`|
|  | `dotnet_naming_style.<styleTitle>.word_separator`|


| Стиль | Описание |
| ------------- |:-------------:|
| Префикс | Обязательные символы, которые должны располагаться перед идентификатором. |
| Суффикс | Обязательные символы, которые должны располагаться после идентификатора. |
| Разделитель слов | Обязательный разделитель между словами в идентификаторе. |
| Регистр букв |`pascal_case`, `camel_case`, `first_word_upper`, `all_upper`, `all_lower` | 

#### <a name="example-editorconfig-file"></a>Пример файла editorconfig:
```
# CSharp formatting settings:
[*.cs]
dotnet_naming_rule.async_methods_end_in_async.style = end_in_async

dotnet_naming_style.end_in_async.required_suffix = Async
dotnet_naming_style.end_in_async.capitalization = pascal_case
``` 

### <a name="example-naming-convention"></a>Пример соглашения об именовании
```
# CSharp formatting settings:
[*.cs]
dotnet_naming_rule.async_methods_end_in_async.symbols  = any_async_methods
dotnet_naming_rule.async_methods_end_in_async.style    = end_in_async
dotnet_naming_rule.async_methods_end_in_async.severity = suggestion

dotnet_naming_symbols.any_async_methods.applicable_kinds           = method
dotnet_naming_symbols.any_async_methods.applicable_accessibilities = *
dotnet_naming_symbols.any_async_methods.required_modifiers         = async

dotnet_naming_style.end_in_async.required_suffix = Async
dotnet_naming_style.end_in_async.capitalization  = pascal_case
``` 

