---
title: Методы и классы Assert MSTest
ms.date: 06/07/2018
ms.topic: reference
helpviewer_keywords:
- Assert classes
- Assert methods
- unit tests, Assert classes
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 41be3aaa4967e4c5f975b43f7d8fec982f04c9b9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659719"
---
# <a name="use-assert-classes-for-unit-testing"></a>Использование классов Assert для модульного тестирования

Классы Assert пространства имен <xref:Microsoft.VisualStudio.TestTools.UnitTesting> служат для проверки определенных функциональных возможностей. Метод модульного теста использует код метода в коде приложения, но сообщает о корректности поведения кода только в том случае, если включены операторы Assert.

## <a name="kinds-of-asserts"></a>Типы классов Assert

В пространстве имен <xref:Microsoft.VisualStudio.TestTools.UnitTesting> имеется несколько типов классов Assert.

В методе теста можно вызывать любые методы класса <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>, например <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType>. Класс <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> содержит много методов для выбора, и многие из этих методов имеют несколько перегрузок.

### <a name="compare-strings-and-collections"></a>Сравнение строк и коллекций

Класс <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert> используется для сравнения коллекций объектов и проверки состояния коллекции.

Класс <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert> используется для сравнения и проверки строк. Этот класс содержит ряд полезных методов, таких как <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=nameWithType>, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Matches%2A?displayProperty=nameWithType> и <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.StartsWith%2A?displayProperty=nameWithType>.

### <a name="exceptions"></a>Исключения

Исключение <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException> возникает в случае неудачного завершения теста. Причиной неудачного завершения теста может быть истечение времени ожидания, непредвиденное исключение или оператор Assert, создающий результат **Сбой**.

Исключение <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException> возникает при каждом тесте с **неопределенным** результатом. Как правило, оператор <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Inconclusive%2A?displayProperty=nameWithType> добавляется к тесту, над которым еще ведется работа, для обозначения его неготовности к выполнению.

> [!NOTE]
> В качестве альтернативы можно пометить тест, который еще не готов к выполнению, атрибутом <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>. Однако в этом случае будет невозможным легко создать отчет по числу тестов, которые еще не реализованы.

При написании нового класса исключения Assert наследование от базового класса <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException> упрощает идентификацию исключения как ошибки подтверждения, а не непредвиденного исключения, выдаваемого тестом или рабочим кодом.

Чтобы проверить, действительно ли вызывается исключение, которое должно вызываться методом в коде приложения, используйте метод <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>.

## <a name="see-also"></a>См. также

- [Модульное тестирование кода](../test/unit-test-your-code.md)