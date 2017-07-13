---
title: "Параметры стиля кода .NET для EditorConfig | Документы Майкрософт"
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
caps.latest.revision: 01
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: 288595f50555bd8314d0ad60cd2e1ce8121a8ab0
ms.contentlocale: ru-ru
ms.lasthandoff: 06/23/2017

---

# Параметры стиля кода .NET для EditorConfig
<a id="net-code-style-settings-for-editorconfig" class="xliff"></a>

## Возможные значения
<a id="possible-values" class="xliff"></a>

`options_name = false|true : none|suggestion|warning|error`

Для параметра стиля кода необходимо указать **true** (предпочитать этот параметр) или **false** (не предпочитать этот параметр), двоеточие (`:`) и уровень серьезности (`none`, `suggestion`, `warning` или `error`). Серьезность означает требуемый уровень выполнения для этого стиля в базе данных кода.

Серьезность | effect
------------ | -------------
Нет | Ничего не показывать пользователю, если этот стиль не соблюдается, однако функции создания кода будут в нем работать. 
suggestion | Если этот стиль не соблюдается, показывать его пользователю как предложение (базовые точки в первых двух символах).
предупреждение | Если этот стиль не соблюдается, выводить предупреждение компилятора.
error | Если этот стиль не соблюдается, выводить ошибку компилятора.

## Параметры стиля кода .NET
<a id="net-code-style-options" class="xliff"></a>

- [Параметры стиля кода .NET](#this_and_me)
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
- [Параметры стиля кода C#](#csharp_codestyle)
    - ["var"](#var)
        - ["var" для встроенных типов](#var_built_in)
        - ["var", если тип является очевидным](#var_apparent)
        - ["var" в другом месте](#var_elsewhere)
    - [Элементы, воплощающие выражение](#expression_bodied_members)
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
    - [Параметры проверки "null"](#null_checking)
        - [Выражения throw](#null_checking_throw_expressions)
        - [Вызовы условного делегата](#null_checking_conditional_delegate_calls)

## <a name="this_and_me">Квалификация "This." и "Me."</a>

### <a name="this_and_me_fields">Поля</a>

|  Имя параметра | `dotnet_style_qualification_for_field` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать, чтобы все нестатические поля, используемые в нестатических методах, предварялись `this.` в C# или `Me.` в Visual Basic. | **C#:** <br>`this.capacity = 0;` <br><br> **Visual Basic:** `Me.capacity = 0`
| False | Предпочитать, чтобы все нестатические поля, используемые в нестатических методах, не предварялись `this.` в C# или `Me.` в Visual Basic. | **C#:** <br>`capacity = 0;` <br><br> **Visual Basic:** `capacity = 0`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_field = false:suggestion
```

### <a name="this_and_me_properties">Свойства</a>

|  Имя параметра | `dotnet_style_qualification_for_property` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать, чтобы все нестатические свойства, используемые в нестатических методах, предварялись `this.` в C# или `Me.` в Visual Basic.| **C#:** <br>`this.ID = 0;` <br><br> **Visual Basic:** `Me.ID = 0`
| False | Предпочитать, чтобы все нестатические свойства, используемые в нестатических методах, *не* предварялись `this.` в C# или `Me.` в Visual Basic. | **C#:** <br>`ID = 0;` <br><br> **Visual Basic:** `ID = 0`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_property = false:suggestion
```


### <a name="this_and_me_methods">Методы</a>
|  Имя параметра | `dotnet_style_qualification_for_method` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать, чтобы все нестатические методы, вызываемые из нестатических методов, предварялись `this.` в C# или `Me.` в Visual Basic.| **C#:** <br>`this.Display();` <br><br> **Visual Basic:** `Me.Display()`
| False | Предпочитать, чтобы все нестатические методы, вызываемые из нестатических методов, *не* предварялись `this.` в C# или `Me.` в Visual Basic. | **C#:** <br>`Display();` <br><br> **Visual Basic:** `Display()`


#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_method = false:suggestion
```

### <a name="this_and_me_events">События</a>
|  Имя параметра | `dotnet_style_qualification_for_event` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать, чтобы все нестатические события, на которые существуют ссылки в нестатических методах, предварялись `this.` в C# или `Me.` в Visual Basic.| **C#:** <br>`this.Elapsed += Handler;` <br><br> **Visual Basic:** `AddHandler Me.Elapsed, AddressOf Handler`
| False | Предпочитать, чтобы все нестатические события, на которые существуют ссылки в нестатических методах, *не* предварялись `this.` в C# или `Me.` в Visual Basic. | **C#:** <br>`Elapsed += Handler;` <br><br> **Visual Basic:** `AddHandler Elapsed, AddressOf Handler`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_event = false:suggestion
```

## <a name="language_keywords">Ключевые слова языка (int, string и т. д.) и имена типов .NET Framework для ссылок на типы</a>
### <a name="language_keywords_variables">Локальные переменные, параметры и элементы</a>
|  Имя параметра | `dotnet_style_predefined_type_for_locals_parameters_members` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Для локальных переменных, параметров и элементов типов предпочитать, чтобы типы с представляющим их ключевым словом языка (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) использовали ключевое слово вместо имени типа (`Int32`, `Int64` и т. д.).| **C#:** <br>`private int _member;` <br><br> **Visual Basic:** `Private _member As Integer`
| False | Для локальных переменных, параметров и элементов типов предпочитать, чтобы типы с представляющим их ключевым словом языка (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) использовали имя типа (`Int32`, `Int64` и т. д.) вместо ключевого слова.  | **C#:** <br>`private Int32 _member;` <br><br> **Visual Basic:** `Private _member As Int32`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
``` 

### <a name="language_keywords_member_access">Выражения доступа к элементам</a>
|  Имя параметра | `dotnet_style_predefined_type_for_member_access` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать ключевое слово при использовании выражения доступа к элементам в типе, представленном ключевым словом (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`).| **C#:** <br>`var local = int.MaxValue;` <br><br> **Visual Basic:** `Dim local = Integer.MaxValue`
| False | Предпочитать имя типа при использовании выражения доступа к элементам в типе, представленном ключевым словом (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`). | **C#:** <br>`var local = Int32.MaxValue;` <br><br> **Visual Basic:** `Dim local = Int32.MaxValue`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

## <a name="expression_level">Настройки уровня выражений</a>
### <a name="expression_level_object_initializers">Инициализаторы объектов</a>
|  Имя параметра | `dotnet_style_object_initializer` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать инициализировать объекты с помощью инициализаторов объектов, когда это возможно.| **C#:** <br>`var c = new Customer(){ Age = 21 };` <br><br> **Visual Basic:** `Dim c = New Customer() With { .Age = 21 }`
| False | Предпочитать *не* инициализировать объекты с помощью инициализаторов объектов. | **C#:** <br>`var c = new Customer();`<br>`c.Age = 21;` <br><br> **Visual Basic:** <br>`Dim c = new Customer() `<br>`c.Age = 21`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_object_initializer = true:suggestion
``` 

### <a name="expression_level_collection_initializers">Инициализаторы коллекций</a>
|  Имя параметра | `dotnet_style_collection_initializer` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать инициализировать коллекции с помощью инициализаторов коллекций, когда это возможно.| **C#:** <br>`var list = new List<int>{ 1, 2, 3 };` <br><br> **Visual Basic:** <br> `Dim list = new List(Of Integer) From { 1, 2, 3}`
| False | Предпочитать *не* инициализировать коллекции с помощью инициализаторов коллекций. | **C#:** <br>`var list = new List<int>();`<br>`list.Add(1);`<br>`list.Add(2);`<br>`list.Add(3);` <br><br> **Visual Basic:** <br>`Dim list = new List(Of Integer)`<br>`list.Add(1)`<br>`list.Add(2)`<br>`list.Add(3)`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_collection_initializer = true:suggestion
```

### <a name="expression_level_tuple_names">Явные имена кортежей</a>
|  Имя параметра | `dotnet_style_explicit_tuple_names` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать имена кортежей свойствам ItemX.| **C#:** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.name;` <br><br> **Visual Basic:** <br> `Dim customer As (name As String, age As Integer) = GetCustomer()`<br>`Dim name = customer.name`
| False | Предпочитать свойства ItemX именам кортежей. | **C#:** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.Item1;` <br><br> **Visual Basic:** <br>`Dim customer As (name As String, age As Integer) = GetCustomer()`<br> `Dim name = customer.Item1`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_explicit_tuple_names = true:suggestion
``` 

### <a name="expression_level_null_checking">Выражения объединения в проверке "null"</a>
|  Имя параметра | `dotnet_style_coalesce_expression` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать выражение объединения со значением NULL проверке тернарного оператора.| **C#:** <br>`var v = x ?? y;` <br><br> **Visual Basic:** <br> `Dim v = If(x, y)`
| False | Предпочитать проверку тернарного оператора выражению объединения со значением NULL. | **C#:** <br>`var v = x != null ? x : y; // or`<br>`var v = x == null ? y : x;` <br><br> **Visual Basic:** <br>`Dim v = If(x Is Nothing, y, x) ' or`<br> `Dim v = If(x IsNot Nothing, x, y)`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_coalesce_expression = true:suggestion
``` 

### <a name="expression_level_null_propogation">Распространение значений NULL в проверке "null"</a>
|  Имя параметра | `dotnet_style_null_propagation` |
| ------------- |:-------------:|
| **Применимые языки** | C# и Visual Basic

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать использовать условный оператор со значением NULL, где это возможно.| **C#:** <br>`var v = o?.ToString();` <br><br> **Visual Basic:** <br> `Dim v = o?.ToString()`
| False | Предпочитать использовать тернарную проверку "null", где это возможно. | **C#:** <br>`var v = o == null ? null : o.ToString(); // or`<br>`var v = o != null ? o.String() : null;` <br><br> **Visual Basic:** <br>`Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or`<br> `Dim v = If(o IsNot Nothing, o.ToString(), Nothing)`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_null_propagation = true:suggestion
``` 

# <a name="csharp_codestyle">Параметры стиля кода C#</a>
## <a name="var">"var"</a>
### <a name="var_built_in">"var" для встроенных типов</a>
|  Имя параметра | `csharp_style_var_for_built_in_types` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать, чтобы `var` использовался для встроенных системных типов, таких как `int`.| **C#:** <br>`var x = 5;`
| False | Предпочитать, чтобы `var` не использовался для встроенных системных типов, таких как `int`. | **C#:** <br>`int x = 5;`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
``` 

### <a name="var_apparent">"var", если тип является очевидным</a>
|  Имя параметра | `csharp_style_var_when_type_is_apparent` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать использовать `var`, если тип уже упоминается в правой части выражения объявления.| **C#:** <br>`var obj = new C();`
| False | Предпочитать не использовать `var`, если тип уже упоминается в правой части выражения объявления. | **C#:** <br>`C obj = new C();`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_var_when_type_is_apparent = true:suggestion
``` 

### <a name="var_elsewhere">"var" в другом месте</a>
|  Имя параметра | `csharp_style_var_elsewhere` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать `var` во всех случаях, если не переопределено другим правилом стиля кода.| **C#:** <br>`var f = this.Init();`
| False | Предпочитать не использовать var во всех случаях, если не переопределено другим правилом стиля кода.| **C#:** <br>`bool f = this.Init();`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_var_elsewhere = true:suggestion
``` 

### <a name="expression_bodied_members">Методы</a>
|  Имя параметра | `csharp_style_expression_bodied_methods` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать элементы, воплощающие выражение, для методов.| **C#:** <br>`public int GetAge() => this.Age;`
| False | Не предпочитать элементы, воплощающие выражение, для методов.| **C#:** <br>`public int GetAge() { return this.Age; }`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
``` 

### <a name="expression_bodied_members_constructors">Конструкторы</a>
|  Имя параметра | `csharp_style_expression_bodied_constructors` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать элементы, воплощающие выражение, для конструкторов.| **C#:** <br>`public Customer(int age) => Age = age;`
| False | Не предпочитать элементы, воплощающие выражение, для конструкторов.| **C#:** <br>`public Customer(int age) { Age = age; }`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_constructors = false:none
``` 

### <a name="expression_bodied_members_operators">Операторы</a>
|  Имя параметра | `csharp_style_expression_bodied_operators` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать элементы, воплощающие выражение, для операторов.| **C#:** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`=> new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);`
| False | Не предпочитать элементы, воплощающие выражение, для операторов.| **C#:** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_operators = false:none
``` 

### <a name="expression_bodied_members_properties">Свойства</a>
|  Имя параметра | `csharp_style_expression_bodied_properties` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать элементы, воплощающие выражение, для свойств.| **C#:** <br>`public int Age => _age;`
| False | Не предпочитать элементы, воплощающие выражение, для свойств.| **C#:** <br>`public int Age { get { return _age; }}`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_properties = false:none
``` 

### <a name="expression_bodied_members_indexers">Индексаторы</a>
|  Имя параметра | `csharp_style_expression_bodied_indexers` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать элементы, воплощающие выражение, для индексаторов.| **C#:** <br>`public T this[int i] => _value[i];`
| False | Не предпочитать элементы, воплощающие выражение, для индексаторов.| **C#:** <br>`public T this[int i] { get { return _values[i]; } }`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_indexers = false:none
``` 

### <a name="expression_bodied_members_accessors">Методы доступа</a>
|  Имя параметра | `csharp_style_expression_bodied_accessors` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать элементы, воплощающие выражение, для методов доступа.| **C#:** <br>`public int Age { get => _age; set => _age = value; }`
| False | Не предпочитать элементы, воплощающие выражение, для методов доступа.| **C#:** <br>`public int Age { get { return _age; } set { _age = value; } }`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_accessors = false:none
``` 

## <a name="pattern_matching">Сопоставление шаблонов</a>
### <a name="pattern_matching_is_cast">"is" с проверкой "cast"</a>
|  Имя параметра | `csharp_style_pattern_matching_over_is_with_cast_check` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать сопоставления шаблонов вместо выражений `is` с приведениями типов.| **C#:** <br>`if (o is int i) {...}`
| False | Предпочитать выражения `is` с приведениями типов вместо сопоставления шаблонов.| **C#:** <br>`if (o is int) {var i = (int)o; ... }`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
```

### <a name="pattern_matching_as_null">"as"с проверкой "null"</a>
|  Имя параметра | `csharp_style_pattern_matching_over_as_with_null_check` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать сопоставление шаблонов вместо выражений `as` с проверками "null", чтобы определить, имеет ли что-то определенный тип.| **C#:** <br>`if (o is string s) {...}`
| False | Предпочитать выражения `as` с проверками "null" вместо соответствия шаблонам, чтобы определить, имеет ли что-то определенный тип.| **C#:** <br>`var s = o as string; if (s != null) {...}`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

### <a name="inlined_variable_declarations">Встроенные объявления переменных</a>
|  Имя параметра | `csharp_style_inlined_variable_declaration` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать встроенное объявление переменных `out`, когда возможно. | **C#:** <br>`if (int.TryParse(value, out int i) {...}`
| False | Предпочитать явное объявление переменных `out`.| **C#:** <br>`int i; if (int.TryParse(value, out i) {...}`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

## <a name="null_checking">Параметры проверки "null"</a>
### <a name="null_checking_throw_expressions">Выражения throw</a>
|  Имя параметра | `csharp_style_throw_expression` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать использовать выражения throw вместо операторов throw. | **C#:** <br>`this.s = ss ?? throw new ArgumentNullException(nameof(s));`
| False | Предпочитать использовать операторы throw вместо выражений throw.| **C#:** <br>`if (s==null) {throw new ArgumentNullException(nameof(s));} this.s = s;`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
```

### <a name="null_checking_conditional_delegate_calls">Предпочитать вызовы условного делегата</a>
|  Имя параметра | `csharp_style_conditional_delegate_call` |
| ------------- |:-------------:|
| **Применимые языки** | C#

| Значение | Описание | Применен 
| ------------- |:-------------|:-------------|
| Да | Предпочитать использовать условную операцию объединения (`?.`) при вызове лямбда-выражения вместо выполнения проверки "null". | **C#:** <br>`func?.Invoke(args);`
| False | Предпочитать выполнять проверку "null" перед вызовом лямбда-выражения вместо использования условного оператора объединения (`?.`).| **C#:** <br>`if (func!=null) { func(args); }`

#### Пример файла editorconfig:
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_conditional_delegate_call = false:suggestion
```

