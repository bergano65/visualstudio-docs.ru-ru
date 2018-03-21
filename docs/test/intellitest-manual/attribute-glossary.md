---
title: "Глоссарий атрибутов | Инструмент тестирования для разработчиков Microsoft IntelliTest | Документы Майкрософт"
ms.date: 05/02/2017
ms.technology: vs-ide-test
ms.topic: article
helpviewer_keywords:
- IntelliTest, Attribute glossary
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 474666d6243f8602c1da55ec113e459d5f2ec1d9
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2018
---
# <a name="attribute-glossary"></a>Глоссарий атрибутов

## <a name="attributes-by-namespace"></a>Список атрибутов по пространству имен

* **Microsoft.Pex.Framework**
  * [PexAssumeNotNull](#pexassumenotnull)
  * [PexClass](#pexclass)
  * [PexGenericArguments](#pexgenericarguments)
  * [PexMethod](#pexmethod)
     - [PexExplorationAttributeBase](#pexexplorationattributebase)<p />

* **Microsoft.Pex.Framework.Settings**
  * [PexAssemblySettings](#pexassemblysettings)<p />

* **Microsoft.Pex.Framework.Instrumentation**
  * [PexAssemblyUnderTest](#pexassemblyundertest)
  * [PexInstrumentAssembly](#pexinstrumentassemblyattribute)<p />

* **Microsoft.Pex.Framework.Using**
  * [PexUseType](#pexusetype)<p />

* **Microsoft.Pex.Framework.Validation**
  * [PexAllowedException](#pexallowedexception)
  * [PexAllowedExceptionFromAssembly](#pexallowedexceptionfromassembly)
  * [PexAllowedExceptionFromType](#pexallowedexceptionfromtype)
  * [PexAllowedExceptionFromTypeUnderTest](#pexallowedexceptionfromtypeundertest)

<a name="pexassumenotnull"></a>
## <a name="pexassumenotnull"></a>PexAssumeNotNull

Этот атрибут утверждает, что управляемое значение не может быть равно **NULL**. Его можно подключить к:

* **параметру** метода параметризованного теста;

  ```
  // assume foo is not null
  [PexMethod]
  public void SomeTest([PexAssumeNotNull]IFoo foo, ...) {}
  ```

* **полю**

  ```
  public class Foo {
     // this field should not be null
     [PexAssumeNotNull]
     public object Bar;
  }
  ```

* **типу**.

  ```
  // never consider null for Foo types
  [PexAssumeNotNull]
  public class Foo {}
  ```

Его также можно подключить к тестовой сборке, тестовой фикстуре или методу теста. В этом случае первые аргументы должны указывать, к какому полю или типу применяются предположения. Если атрибут применяется к типу, он применяется ко всем полям с таким формальным типом.

<a name="pexclass"></a>
## <a name="pexclass"></a>PexClass

Этот атрибут помечает класс, который содержит *изучения*. Это эквивалент **TestClassAttribute** в платформе MSTest (или **TestFixtureAttribute** в платформе NUnit). Этот атрибут является необязательным.

Классы, помеченные с помощью [PexClass](#pexclass), должны быть *конструируемыми по умолчанию*:

* открыто экспортируемый тип
* конструктор по умолчанию
* не абстрактный

Если класс не удовлетворяет этим требованиям, возвращается ошибка, а исследование завершается со сбоем.

Настоятельно рекомендуется сделать эти классы **частичными**, чтобы IntelliTest мог создавать тесты, являющиеся частью класса, но находящиеся в отдельном файле. Такой подход решает многие проблемы, связанные с [видимостью](input-generation.md#visibility), и является стандартным приемом в C#.

**Дополнительный набор и категории**:

```
[TestClass] // MSTest test fixture attribute
[PexClass(Suite = "checkin")] // fixture attribute
public partial class MyTests { ... }
```

**Указание тестируемого типа**:

```
[PexClass(typeof(Foo))] // this is a test for Foo
public partial class FooTest { ... }
```

Класс может содержать методы, помеченные с помощью [PexMethod](#pexmethod). IntelliTest также поддерживает [методы подготовки и демонтажа](test-generation.md#setup-teardown).

<a name="pexgenericarguments"></a>
## <a name="pexgenericarguments"></a>PexGenericArguments

Этот атрибут предоставляет кортеж типов для создания экземпляра [универсального параметризованного модульного теста](test-generation.md#generic-parameterized).

<a name="pexmethod"></a>
## <a name="pexmethod"></a>PexMethod

Этот атрибут помечает метод как [параметризованный модульный тест](test-generation.md#parameterized-unit-testing).
Метод должен находиться внутри класса, помеченного атрибутом [PexClass](#pexclass).

IntelliTest создаст традиционные тесты без параметров, вызывающие [параметризованный модульный тест](test-generation.md#parameterized-unit-testing) с разными параметрами.

Параметризованный модульный тест:

* должен быть методом экземпляра;
* должен быть [видимым](input-generation.md#visibility) для тестового класса, в который помещаются созданные тесты согласно [каскаду параметров](settings-waterfall.md);
* может принимать любое число параметров;
* может быть универсальным.

**Пример**

```
[PexClass]
public partial class MyTests {
     [PexMethod]
     public void MyTest(int i)
     { ... }
}
```

<a name="pexexplorationattributebase"></a>
## <a name="pexexplorationattributebase"></a>PexExplorationAttributeBase

[Дополнительные сведения](https://msdn.microsoft.com/library/microsoft.pex.framework.pexexplorationattributebase.aspx)

<a name="pexassemblysettings"></a>
## <a name="pexassemblysettings"></a>PexAssemblySettings

Этот атрибут можно задать на уровне сборки, чтобы переопределить значения параметров по умолчанию для всех исследований.

```
using Microsoft.Pex.Framework;
// overriding the test framework selection
[assembly: PexAssemblySettings(TestFramework = "Naked")]
```

<a name="pexassemblyundertest"></a>
## <a name="pexassemblyundertest"></a>PexAssemblyUnderTest

Этот атрибут указывает сборку, проверяемую текущим тестовым проектом. 

```
[assembly: PexAssemblyUnderTest("MyAssembly")]
```

<a name="pexinstrumentassemblyattribute"></a>
## <a name="pexinstrumentassemblyattribute"></a>PexInstrumentAssemblyAttribute

Этот атрибут используется для указания инструментируемой сборки.

**Пример**

```
using Microsoft.Pex.Framework;

// the assembly containing ATypeFromTheAssemblyToInstrument should be instrumented
[assembly: PexInstrumentAssembly(typeof(ATypeFromTheAssemblyToInstrument))]

// the assembly name can be used as well
[assembly: PexInstrumentAssembly("MyAssemblyName")]
```

<a name="pexusetype"></a>
## <a name="pexusetype"></a>PexUseType

Этот атрибут сообщает IntelliTest, что можно использовать определенный тип для создания экземпляров (абстрактных) базовых типов или интерфейсов.

**Пример**

```
[PexMethod]
[PexUseType(typeof(A))]
[PexUseType(typeof(B))]
public void MyTest(object testParameter)
{
     ... // IntelliTest will consider types A and B to instantiate 'testParameter'
}
```

<a name="pexallowedexception"></a>
## <a name="pexallowedexception"></a>PexAllowedException

Если этот атрибут подключен к [PexMethod](#pexmethod) (или [PexClass](#pexclass)), он по умолчанию изменяет логику IntelliTest, которая определяет неудачное выполнение тестов. Тест не будет рассматриваться как непройденный, даже если он выдает указанное исключение.

**Пример**

Следующий тест указывает, что конструктор **Stack** может вызывать исключение **ArgumentOutOfRangeException**:

```
class Stack {
  int[] _elements;
  int _count;
  public Stack(int capacity) {
    if (capacity<0) throw new ArgumentOutOfRangeException();
    _elements = new int[capacity];
    _count = 0;
  }
  ...
}
```

Фильтр подключен к фикстуре следующим образом (он может также быть определен на уровне сборки или тестирования):

```
[PexMethod]
[PexAllowedException(typeof(ArgumentOutOfRangeException))]
class CtorTest(int capacity) {
  Stack s = new Stack(capacity); // may throw ArgumentOutOfRangeException
}
```

<a name="pexallowedexceptionfromassembly"></a>
## <a name="pexallowedexceptionfromassembly"></a>PexAllowedExceptionFromAssembly

[Дополнительные сведения](https://msdn.microsoft.com/library/microsoft.pex.framework.validation.pexallowedexceptionfromassemblyattribute.aspx)

<a name="pexallowedexceptionfromtype"></a>
## <a name="pexallowedexceptionfromtype"></a>PexAllowedExceptionFromType

[Дополнительные сведения](https://msdn.microsoft.com/library/microsoft.pex.framework.validation.pexallowedexceptionfromtypeattribute.aspx)

<a name="pexallowedexceptionfromtypeundertest"></a>
## <a name="pexallowedexceptionfromtypeundertest"></a>PexAllowedExceptionFromTypeUnderTest

[Дополнительные сведения](https://msdn.microsoft.com/library/microsoft.pex.framework.validation.pexallowedexceptionfromtypeundertestattribute.aspx)

## <a name="got-feedback"></a>Хотите оставить отзыв?

Публикуйте свои идеи и запросы функций на сайте **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
