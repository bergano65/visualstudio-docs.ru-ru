---
title: Обзор | Инструмент тестирования для разработчиков Microsoft IntelliTest
description: Узнайте, как IntelliTest использует автоматизированный и прозрачный подход к тестированию, что позволяет сформировать набор кандидатов на тесты для кода .NET.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Visual Studio IntelliTest developer testing tool
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 856c730720be83571798819feae66eb6080f200b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920589"
---
# <a name="overview-of-microsoft-intellitest"></a>Обзор Microsoft IntelliTest

IntelliTest позволяет находить ошибки на раннем этапе и уменьшает затраты на обслуживание тестирования. Благодаря автоматизированному и прозрачному подходу к тестированию инструмент IntelliTest позволяет сформировать набор кандидатов на тесты для кода .NET. Создание набора тестов можно дополнительно настроить с помощью задаваемых вами *свойств правильности*. IntelliTest даже будет автоматически модифицировать набор тестов по мере модификации тестируемого кода.

> [!NOTE]
> Инструмент IntelliTest доступен только в выпуске Enterprise. Он поддерживается только для кода C#, предназначенного для .NET Framework. В настоящее время инструмент не поддерживается для .NET Core и .NET Standard.

**Характеристические тесты**. IntelliTest позволяет определить поведение кода в рамках набора традиционных модульных тестов.
Подобный набор тестов можно использовать в качестве набора регрессии, чтобы сформировать основу для преодоления сложностей, связанных с рефакторингом незнакомого кода или кода прежних версий.

**Управляемое создание входных данных для теста**. Инструмент IntelliTest использует открытый подход к анализу кода и поиску решений для ограничений, чтобы автоматически создавать точные входные значения для тестов, при этом вмешательство пользователя обычно не требуется. Для сложных типов объектов он автоматически создает фабрики. Вы можете управлять созданием входных данных для теста, расширяя и настраивая фабрики в соответствии с вашими требованиями. Свойства правильности, заданные в коде в качестве утверждений, также будут автоматически использоваться для дальнейшего управления созданием входных данных.

**Интеграция со средой IDE**. Инструмент IntelliTest полностью интегрирован в среду IDE Visual Studio. Все данные, собранные во время создания набора тестов (например, автоматически созданные входные данные, выходные данные кода, созданные тестовые случаи и состояние их выполнения), отображаются в интегрированной среде разработки Visual Studio. Вы можете легко переключаться между правкой кода и повторным выполнением IntelliTest, не выходя из среды IDE Visual Studio.
Тесты можно сохранить в качестве решения — проекта модульных тестов, после чего их автоматически определит обозреватель тестов Visual Studio.

**Дополнение существующих методик тестирования**. Используйте IntelliTest в дополнение к уже имеющимся методикам тестирования.

Если вы хотите тестировать:

* Алгоритмы для примитивных типов данных или массивы примитивных типов данных:
  * напишите [параметризованные модульные тесты](test-generation.md#parameterized-unit-testing).
* Алгоритмы для сложных типов данных, таких как компилятор:
  * сначала позвольте IntelliTest создать абстрактное представление данных, а затем передайте его в алгоритм;
  * позвольте IntelliTest собрать экземпляры с помощью [создания настраиваемых объектов](input-generation.md#objects) и инвариантов данных, а затем вызовите этот алгоритм.
* Контейнеры данных:
  * напишите [параметризованные модульные тесты](test-generation.md#parameterized-unit-testing);
  * позвольте IntelliTest собрать экземпляры с помощью [создания настраиваемых объектов](input-generation.md#objects) и инвариантов данных, а затем вызовите метод контейнера и перепроверьте инварианты;
  * напишите [параметризованные модульные тесты](test-generation.md#parameterized-unit-testing), вызывающие разные методы реализации в зависимости от значений параметров.
* Существующую базу кода:
  * используйте мастер IntelliTest в Visual Studio, чтобы для начала создать набор [параметризованных модульных тестов (PUT)](test-generation.md#parameterized-unit-testing).

## <a name="the-hello-world-of-intellitest"></a>Основы IntelliTest

Инструмент IntelliTest находит входные данные, относящиеся к тестируемой программе, поэтому его можно использовать для создания всем известной строки **Hello World** . Здесь предполагается, что вы создали проект тестов C# на основе MSTest и добавили ссылку на **Microsoft.Pex.Framework**. При использовании другой платформы тестирования создайте библиотеку классов C# и прочитайте о настройке проекта в документации к этой платформе тестирования.

Приведенный ниже пример создает два ограничения для параметра **value**, чтобы инструмент IntelliTest создал требуемую строку:

```csharp
using System;
using Microsoft.Pex.Framework;
using Microsoft.VisualStudio.TestTools.UnitTesting;

[TestClass]
public partial class HelloWorldTest {
    [PexMethod]
    public void HelloWorld([PexAssumeNotNull]string value) {
        if (value.StartsWith("Hello")
            && value.EndsWith("World!")
            && value.Contains(" "))
            throw new Exception("found it!");
    }
}
```

После компиляции и выполнения IntelliTest создает набор тестов, например следующего вида:

1. ""
2. "\0\0\0\0\0"
3. "Hello"
4. "\0\0\0\0\0\0"
5. "Hello\0"
6. "Hello\0\0"
7. "Hello\0World!"
8. "Hello World!"

> [!NOTE]
> При возникновении проблем со сборкой попробуйте заменить ссылки на Microsoft.VisualStudio.TestPlatform.TestFramework и Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions ссылками на Microsoft.VisualStudio.QualityTools.UnitTestFramework.

Сведения о сохранении созданных тестов см. в статье [Создание модульных тестов для кода с помощью IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md). Созданный тестовый код должен содержать следующий код:

```csharp
[TestMethod]
[PexGeneratedBy(typeof(global::HelloWorldTest))]
[PexRaisedException(typeof(Exception))]
public void HelloWorldThrowsException167()
{
    this.HelloWorld("Hello World!");
}
```

Все просто!

Дополнительные ресурсы:
  * посмотрите [видео на Channel 9](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest)
  * прочитайте этот [обзор в журнале MSDN](/archive/msdn-magazine/2015/february/visual-studio-2015-build-better-software-with-smart-unit-tests)

## <a name="important-attributes"></a>Важные атрибуты

* [PexClass](attribute-glossary.md#pexclass) помечает тип, содержащий **PUT**.
* [PexMethod](attribute-glossary.md#pexmethod) помечает **PUT**.
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) помечает параметр, отличный от NULL.

```csharp
using Microsoft.Pex.Framework;

[..., PexClass(typeof(Foo))]
public partial class FooTest {
    [PexMethod]
    public void Bar([PexAssumeNotNull]Foo target, int i) {
        target.Bar(i);
    }
}
```

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) привязывает тестовый проект к проекту.
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) указывает сборку для инструментирования.

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="important-static-helper-classes"></a><a name="helper-classes"></a> Важные статические вспомогательные классы

* [PexAssume](static-helper-classes.md#pexassume) вычисляет предположения (фильтрация ввода).
* [PexAssert](static-helper-classes.md#pexassert) вычисляет утверждения.
* [PexChoose](static-helper-classes.md#pexchoose) создает новые варианты (дополнительные входные данные).
* [PexObserve](static-helper-classes.md#pexobserve) регистрирует динамические значения для созданных тестов.

```csharp
[PexMethod]
void StaticHelpers(Foo target) {
    PexAssume.IsNotNull(target);

    int i = PexChoose.Value<int>("i");
    string result = target.Bar(i);

    PexObserve.ValueForViewing<string>("result", result);
    PexAssert.IsNotNull(result);
}
```

## <a name="limitations"></a>Ограничения

Этот раздел описывает ограничения инструмента IntelliTest:

* [Недетерминированность](#nondeterminism)
* [Параллелизм](#concurrency)
* [Машинный код .NET](#native-code)
* [Платформа](#platform)
* [Язык](#language)
* [Символьная аналитика](#symbolic-reasoning)
* [Трассировки стека](#incorrect-stack-traces)

### <a name="nondeterminism"></a>Недетерминированность

IntelliTest предполагает, что анализируемая программа является детерминированной. Если это не так, IntelliTest выполняется в цикле, пока не достигнет границы исследования.

IntelliTest считает программу недетерминированной, если она зависит от входных данных, которые IntelliTest не может контролировать.

IntelliTest управляет входными данными для [параметризованных модульных тестов](test-generation.md#parameterized-unit-testing), полученными из [PexChoose](static-helper-classes.md#pexchoose).
В этом смысле результаты вызовов неуправляемого или неинструментированного кода также считаются "входными данными" для инструментируемой программы, однако IntelliTest не может управлять ими. Если поток управления программы зависит от конкретных значений, поступающих из таких внешних источников, IntelliTest не может "направить" программу в неизученные ранее области.

Кроме того, программа считается недетерминированной, если значения из внешних источников изменяются при повторном запуске программы. В таких случаях IntelliTest утрачивает контроль над выполнением программы, и поиск становится неэффективным.

Возникновение подобной ситуации не всегда очевидно. Рассмотрим следующие примеры:

* Результат метода **GetHashCode()** предоставляется неуправляемым кодом и не является прогнозируемым.
* Класс **System.Random** использует текущее системное время для предоставления действительно случайных значений.
* Класс **System.DateTime** предоставляет текущее время, которое не контролируется IntelliTest.

### <a name="concurrency"></a>параллелизм

IntelliTest не обрабатывает многопоточные программы.

### <a name="native-code"></a>Машинный код

Инструмент IntelliTest не поддерживает машинный код, например инструкции x86, вызываемые с помощью **P/Invoke**. Он не способен преобразовывать такие вызовы в ограничения, которые можно передать в [поиск решений для ограничений](input-generation.md#constraint-solver).
Даже для кода .NET он способен анализировать лишь тот код, который сам инструментирует. IntelliTest не может инструментировать определенные части **mscorlib**, включая библиотеку отражения. **DynamicMethod** невозможно инструментировать.

Предлагаемый обходной путь заключается в использовании тестового режима, при котором такие методы находятся в типах в динамической сборке. Однако даже если некоторые методы являются неинструментированными, IntelliTest попытается охватить как можно больше инструментированного кода.

### <a name="platform"></a>Платформа

IntelliTest поддерживается только на 32-разрядной платформе .NET Framework (x86).

### <a name="language"></a>Язык

По сути, IntelliTest способен анализировать произвольные программы .NET, написанные на любом языке .NET. Однако в Visual Studio поддерживается только C#.

### <a name="symbolic-reasoning"></a>Символьная аналитика

IntelliTest использует автоматический [поиск решений для ограничений](input-generation.md#constraint-solver), чтобы определить релевантные значения для теста и тестируемой программы. Однако возможности поиска решений для ограничений были и всегда будут довольно ограничены.

### <a name="incorrect-stack-traces"></a>Неправильные трассировки стека

Так как IntelliTest перехватывает и пересоздает исключения в каждом инструментированном методе, номера строк в трассировках стека будут неправильными. Такое ограничение изначально заложено в инструкцию повторного создания.

## <a name="further-reading"></a>Дополнительные сведения

* [Запись блога с общими сведениями](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/).
* [Создание модульных тестов для кода с помощью IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md)