---
title: "Создание теста | Инструмент тестирования для разработчиков Microsoft IntelliTest | Документы Майкрософт"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Test generation
ms.assetid: B6CADFD1-42C7-4FC0-B41F-0E9F8291A702
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.openlocfilehash: 5bc8b15d2bd8de53cabc11986e9e848aea973c39
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="test-generation"></a>Создание теста

При традиционном модульном тестировании для создания теста требуется несколько компонентов:

```
[Test]
void MyTest() {
    // data
    ArrayList a = new ArrayList();

    // method sequence
    a.Add(5);

    // assertions
    Assert.IsTrue(a.Count==1);
    Assert.AreEqual(a[0], 5);
}
```

Тест включает в себя различные аспекты:

* Он задает [последовательность вызовов методов](test-generation.md#test-generators).
* Он задает аргументы, с помощью которых эти методы вызываются. Эти аргументы являются [входными данными теста](input-generation.md).
* Он проверяет правильность поведения тестируемого приложения, задавая набор [утверждений](#assumptions-and-assertions).

Часто IntelliTest может автоматически определить значения соответствующих аргументов для более общих [параметризованных модульных тестов](#parameterized-unit-testing), предоставляющих последовательность вызовов методов и утверждений.

<a name="test-generators"></a>
## <a name="test-generators"></a>Генераторы тестов

IntelliTest создает тестовые случаи, выбирая последовательность методов реализации в рамках выполняемого теста, а затем формируя входные данные для этих методов с проверкой утверждений по полученным данным.

В основной части [параметризованного модульного теста](#parameterized-unit-testing) явно задается последовательность вызовов методов.

Когда IntelliTest требуется создать объекты, вызовы конструкторов и фабричных методов автоматически добавляются в последовательность по мере необходимости.

<a name="parameterized-unit-testing"></a>
## <a name="parameterized-unit-testing"></a>Параметризованное модульное тестирование

*Параметризованные модульные тесты* (PUT) — это тесты, принимающие параметры. В отличие от обычных модульных тестов, которые обычно являются методами closed, параметризованные модульные тесты принимают любой набор параметров. Неужели все так просто? Да, IntelliTest попытается [создать (минимальный) набор входных данных](input-generation.md), который [полностью охватывает](input-generation.md#dynamic-code-coverage) доступный тесту код.

Параметризованные модульные тесты определяются с помощью настраиваемого атрибута [PexMethod](attribute-glossary.md#pexmethod) по аналогии с MSTest (или NUnit, xUnit). Тесты PUT — это методы экземпляра, логически сгруппированные по классам с меткой [PexClass](attribute-glossary.md#pexclass). Следующий пример показывает простой тест PUT, хранящийся в классе **MyPexTest**:

```
[PexMethod]
void ReplaceFirstChar(string target, char c) {

    string result = StringHelper.ReplaceFirstChar(target, c);

    Assert.AreEqual(result[0], c);
}
```

где **ReplaceFirstChar** — это метод, заменяющий первый символ строки:

```
class StringHelper {
    static string ReplaceFirstChar(string target, char c) {
        if (target == null) throw new ArgumentNullException();
        if (target.Length == 0) throw new ArgumentOutOfRangeException();
        return c + target.Substring(1);
    }
}
```

Из этого теста IntelliTest может автоматически [создать входные данные](input-generation.md) для теста PUT, охватывающего множество путей выполнения тестируемого кода. Каждый входной параметр, охватывающий отдельный путь выполнения, сериализуется как модульный тест:

```
[TestMethod, ExpectedException(typeof(ArgumentNullException))]
void ReplaceFirstChar0() {
    this.ReplaceFirstChar(null, 0);
}
...
[TestMethod]
void ReplaceFirstChar10() {
    this.ReplaceFirstChar("a", 'c');
}
```

<a name="generic-parameterized"></a>
## <a name="generic-parameterized-unit-testing"></a>Общее параметризованное модульное тестирование

Параметризованные модульные тесты могут быть универсальными методами. В этом случае пользователю нужно указать типы, используемые для создания экземпляра метода, с помощью [PexGenericArguments](attribute-glossary.md#pexgenericarguments).

```
[PexClass]
public partial class ListTest {
    [PexMethod]
    [PexGenericArguments(typeof(int))]
    [PexGenericArguments(typeof(object))]
    public void AddItem<T>(List<T> list, T value)
    { ... }
}
```

<a name="allowing-exceptions"></a>
## <a name="allowing-exceptions"></a>Разрешение исключений

IntelliTest предоставляет множество атрибутов проверки для рассмотрения исключений и их разделения на ожидаемые и непредвиденные.

Ожидаемые исключения создают негативные тестовые случаи с соответствующей аннотацией, например **ExpectedException(typeof(*xxx*))**, а непредвиденные исключения создают неудачные тестовые случаи.

```
[PexMethod, PexAllowedException(typeof(ArgumentNullException))]
void SomeTest() {...}
```

Используются следующие проверяющие элементы управления:

* [PexAllowedException](attribute-glossary.md#pexallowedexception): разрешает конкретный тип исключений из любого места.
* [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly): разрешает конкретный тип исключений из указанной сборки.
* [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype): разрешает конкретный тип исключений из указанного типа.
* [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest): разрешает конкретный тип исключений из тестируемого типа.

<a name="internal-types"></a>
## <a name="testing-internal-types"></a>Тестирование внутренних типов

Инструмент IntelliTest может тестировать внутренние типы при условии, что они ему видны. Чтобы IntelliTest мог видеть типы, мастера IntelliTest Visual Studio добавляют в ваш проект теста или продукта следующий атрибут тестирования:

```
[assembly: InternalsVisibleTo("Microsoft.Pex, PublicKey=002400000480000094000000060200000024000052534131000400000100010007d1fa57c4aed9f0a32e84aa0faefd0de9e8fd6aec8f87fb03766c834c99921eb23be79ad9d5dcc1dd9ad236132102900b723cf980957fc4e177108fc607774f29e8320e92ea05ece4e821c0a5efe8f1645c4c0c93c1ab99285d622caa652c1dfad63d745d6f2de5f17e5eaf0fc4963d261c8a12436518206dc093344d5ad293
```

<a name="assumptions-and-assertions"></a>
## <a name="assumptions-and-assertions"></a>Предположения и утверждения

Пользователи могут использовать предположения и утверждения, чтобы задать [предусловия](#precondition) (предположения) и [постусловия](#postcondition) (утверждения) для своих тестов. Когда IntelliTest создает набор значений параметров и "изучает" код, он может нарушить предположение теста. В этом случае инструмент не создает тест для этого пути, а автоматически пропускает его.

Концепция утверждений хорошо известна в рамках платформы обычного модульного тестирования, поэтому IntelliTest может работать со встроенными классами **Assert**, предоставляемыми каждой поддерживаемой платформой тестирования. Однако большинство платформ не предоставляют класс **Assume**. В этом случае IntelliTest предоставляет класс [PexAssume](static-helper-classes.md#pexassume). Если вы не хотите использовать существующую платформу тестирования, в IntelliTest также есть класс [PexAssert](static-helper-classes.md#pexassert).

```
[PexMethod]
public void Test1(object o) {
    // precondition: o should not be null
    PexAssume.IsNotNull(o);

    ...
}
```

В частности, отличное от NULL допущение можно закодировать в качестве настраиваемого атрибута:

```
[PexMethod]
public void Test2([PexAssumeNotNull] object o)
// precondition: o should not be null
{
   ...
}
```

<a name="precondition"></a>
## <a name="precondition"></a>Предусловие

Предусловие метода указывает условия, при которых метод выполняется успешно.

Обычно предусловие реализуется за счет проверки параметров и состояния объекта и вызывает исключение **ArgumentException** или **InvalidOperationException** при нарушении.

В IntelliTest предусловие [параметризованного модульного теста](#parameterized-unit-testing) выражается с помощью [PexAssume](static-helper-classes.md#pexassume).

<a name="postcondition"></a>
## <a name="postcondition"></a>Постусловие

Постусловие метода выражает условия, которые нужно хранить во время и после выполнения метода, предполагая, что его предусловия изначально были допустимыми.

Обычно постусловие реализуется путем вызова методов **Assert**.

В IntelliTest постусловие [параметризованного модульного теста](#parameterized-unit-testing) выражается с помощью [PexAssert](static-helper-classes.md#pexassert).

<a name="test-failures"></a>
## <a name="test-failures"></a>Сбои при тестировании
Каковы условия сбоя созданного теста?

1. Когда тест не завершается в рамках [настроенных границ пути](exploration-bounds.md), он считается неудачным, если только не задан параметр [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded).

1. Если тест выдает исключение **PexAssumeFailedException**, он завершается успешно. Однако обычно эти сведения отфильтровываются, если только для [TestEmissionFilter](exploration-bounds.md#testemissionfilter) не задано значение **All**

1. Если тест нарушает [утверждение](#assumptions-and-assertions), например, выдавая исключение о нарушении утверждения для платформы модульного тестирования, он завершается неудачно.

Если ни один из приведенных выше вариантов не позволяет принять решение, тест завершается успешно только в том случае, когда не вызывает исключение. Нарушения утверждений обрабатываются аналогично исключениям.

<a name="setup-teardown"></a>
## <a name="setup-and-tear-down"></a>Подготовка и демонтаж

В рамках интеграции с платформами тестирования IntelliTest поддерживает обнаружение и запуск подготовки и демонтажа методов.

**Пример**

```
using Microsoft.Pex.Framework;
using NUnit.Framework;

namespace MyTests
{
    [PexClass]
    [TestFixture]
    public partial class MyTestClass
    {
        [SetUp]
        public void Init()
        {
            // monitored
        }

        [PexMethod]
        public void MyTest(int i)
        {
        }

        [TearDown]
        public void Dispose()
        {
            // monitored
        }
    }
}

```

<a name="further-reading"></a>
## <a name="further-reading"></a>Дополнительные сведения

* [Привязка теста к коду](https://blogs.msdn.microsoft.com/visualstudioalm/2015/04/18/smart-unit-tests-test-to-code-binding-test-case-management/)
* [Один тест на любой случай](https://blogs.msdn.microsoft.com/visualstudioalm/2015/07/05/intellitest-one-test-to-rule-them-all/)

## <a name="got-feedback"></a>Хотите оставить отзыв?

Публикуйте свои идеи и запросы функций на сайте **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
