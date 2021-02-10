---
title: Статические вспомогательные классы | Инструмент тестирования для разработчиков Microsoft IntelliTest
description: Узнайте о статических вспомогательных классах, которые IntelliTest предоставляет для создания параметризованных модульных тестов.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Static helper classes
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 41d059d4346cb3a19564c539f6f427961810cd05
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916465"
---
# <a name="static-helper-classes"></a>Статические вспомогательные классы

IntelliTest предоставляет набор статических вспомогательных классов, который можно использовать при создании [параметризованных модульных тестов](test-generation.md#parameterized-unit-testing):

* [PexAssume](#pexassume): используется для определения предположений для входных данных, а также удобен при фильтрации нежелательных входных данных.
* [PexAssert](#pexassert): простой класс утверждения, используемый, когда в вашей платформе тестирования отсутствует подобный класс.
* [PexChoose](#pexchoose): поток дополнительных входных данных теста, которыми управляет IntelliTest.
* [PexObserve](#pexobserve) регистрирует конкретные значения и при необходимости проверяет их в созданном коде.

Некоторые классы позволяют осуществлять низкоуровневое взаимодействие с модулем формирования рассуждений IntelliTest:

* [PexSymbolicValue](#pexsymbolicvalue): служебные программы для проверки или изменения символьных ограничений для переменных.

<a name="pexassume"></a>
## <a name="pexassume"></a>PexAssume

Статический класс, используемый для выражения предположений, например [предусловий](test-generation.md#precondition), в [параметризованных модульных тестах](test-generation.md#parameterized-unit-testing). Методы этого класса можно использовать для фильтрации нежелательных вводных значений теста.

Если подразумеваемое условие не соблюдается для определенных входных данных теста, возникает исключение **PexAssumeFailedException**, из-за которого тест игнорируется без уведомления.

**Пример**

Следующий параметризованный тест не будет учитывать **j=0**:

```csharp
public void TestSomething(int i, int j) {
     PexAssume.AreNotEqual(j, 0);
     int k = i/j;
     ...
}
```

**Замечания**

Приведенный выше код почти полностью эквивалентен следующему:

```csharp
     if (j==0)
          return;
```

за исключением того, что неудачное выполнение **PexAssume** не дает тестовые случаи. В случае оператора **if** IntelliTest создает отдельный тестовый случай для охвата ветви **then** в операторе **if**.

**PexAssume** также содержит специальные вложенные классы для использования предположений по строкам, массивам и коллекциям.

<a name="pexassert"></a>
## <a name="pexassert"></a>PexAssert

Статический класс, используемый для выражения утверждений, например [постусловий](test-generation.md#postcondition), в [параметризованных модульных тестах](test-generation.md#parameterized-unit-testing).

Если утвержденное условие не соблюдается для определенных входных данных теста, возникает исключение **PexAssertFailedException**, вызывающее сбой теста.

**Пример**

Следующий код утверждает, что модуль целого числа является положительным:

```csharp
public void TestSomething(int i) {
     int j = Maths.Abs(i);
     PexAssert.IsTrue(j >= 0);
     ...
}
```

<a name="pexchoose"></a>
## <a name="pexchoose"></a>PexChoose

Статический класс, предоставляющий тесту вспомогательные входные значения, которые можно использовать для реализации [параметризованных макетов](input-generation.md#parameterized-mocks).

Класс **PexChoose** не помогает установить, пройден ли тест для определенных вводных значений. **PexChoose** просто предоставляет входные значения, которые также называются *вариантами*. Пользователь по-прежнему самостоятельно ограничивает входные значения и пишет утверждения, определяющие, пройден ли тест.

**Режимы работы**

Существуют два режима работы класса **PexChoose**:

* Когда IntelliTest выполняет символьный анализ теста и тестируемого кода во время [создания входных данных](input-generation.md), средство выбора возвращает произвольные значения, а IntelliTest отслеживает использование каждого значения в тесте и тестируемом коде. IntelliTest создаст соответствующие значения для запуска активации разных путей выполнения в тесте и тестируемом коде.

* Созданный код для конкретных тестовых случаев определенным образом задает поставщика вариантов, чтобы при повторном выполнении такого тестового случая выбирались конкретные варианты для активации определенного пути выполнения.

**Использование**

* Простой вызов **PexChoose.Value** для создания нового значения:

```csharp
public int Foo() {
    return PexChoose.Value<int>("foo");
}
```

<a name="pexobserve"></a>
## <a name="pexobserve"></a>PexObserve

Статический класс для регистрации именованных значений.

Когда IntelliTest изучает код, **PexObserve** используется для записи вычисляемых значений с помощью их форматированных строковых представлений. Эти значения сопоставляются с уникальными именами.

```csharp
PexObserve.Value<string>("result", result);
```

**Пример**

```csharp
// product code
public static class MathEx {
     public static int Square(int value) { return value * value; }
}

// fixture
[TestClass]
public partial class MathExTests {
     [PexMethod]
     public int SquareTest(int a) {
        int result = MathEx.Square(a);
        // storing result
        return result;
     }
}
```

<a name="pexsymbolicvalue"></a>
## <a name="pexsymbolicvalue"></a>PexSymbolicValue

Статический класс, позволяющий игнорировать ограничения параметров, а также выводить связанную со значениями символьную информацию.

**Использование**

В общем случае IntelliTest пытается охватить все пути выполнения кода во время выполнения. Однако в том числе и при вычислении условий предположений и утверждений ему не следует изучать все возможные случаи.

**Пример**

Этот пример показывает реализацию метода **PexAssume.Arrays.ElementsAreNotNull**.
В этом методе игнорируются ограничения, накладываемые на длину массива, чтобы помешать IntelliTest создать различные размеры массива. Ограничения игнорируются только здесь. Если тестируемый код ведет себя по-разному для разных длин массива, IntelliTest не может создавать массивы разного размера из ограничений тестируемого кода.

```csharp
public static void AreElementsNotNull<T>(T[] value)
    where T : class
{
    PexAssume.NotNull(value);
    // the followings prevents the exploration of all array lengths
    int len = PexSymbolicValue.Ignore<int>(value.Length);

    // building up a boolean value as follows prevents exploration
    // of all combinations of non-null (instead, there are just two cases)
    bool anyNull = false;
    for (int i = 0; i < len; ++i)
        anyNull |= value[i] == null;

    // was any element null?
    if (anyNull)
        PexAssume.Fail("some element of array is a null reference");
}
```

## <a name="got-feedback"></a>Хотите отправить отзыв?

Делитесь своими идеями и пожеланиями относительно новых функций в [сообществе разработчиков](https://aka.ms/feedback/suggest?space=8).
