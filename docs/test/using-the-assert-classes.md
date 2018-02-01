---
title: "Использование классов Assert | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Assert classes
- Assert statements
- unit tests, Assert statements
- unit tests, Assert classes
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 01d41202f49a61a1ae2ba0f926b5c5b563ab351c
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="using-the-assert-classes"></a>Использование классов Assert
Классы Assert пространства имен UnitTestingFramework служат для проверки определенных функциональных возможностей. Метод модульного теста использует код метода в коде разработки, но докладывает о корректности поведения кода только в том случае, если включены операторы Assert.  
  
## <a name="kinds-of-asserts"></a>Типы классов Assert  
 В пространстве имен <xref:Microsoft.VisualStudio.TestTools.UnitTesting> имеется несколько типов классов Assert.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>  
  
 В методе теста можно вызывать любое число методов класса Assert, таких как Assert.AreEqual(). Класс Assert содержит много методов для выбора, и многие из этих методов имеют несколько перегрузок.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>  
  
 Класс CollectionAssert служит для сравнения коллекций объектов и проверки состояния одной или нескольких коллекций.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>  
  
 Класс StringAssert служит для сравнения строк. Этот класс содержит различные полезные методы, такие как StringAssert.Contains, StringAssert.Matches и StringAssert.StartsWith.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>  
  
 Исключение AssertFailedException возникает в случае невыполнения теста. Причиной невыполнения теста может быть истечение времени ожидания, непредвиденное исключение или оператор Assert, создающий результат "Ошибка".  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>  
  
 Исключение AssertInconclusiveException возникает при каждом тесте с неопределенным результатом. Как правило, оператор Assert.Inconclusive добавляется к тесту, над которым еще ведется работа, для обозначения его неготовности к выполнению.  
  
> [!NOTE]
>  Альтернативным вариантом может быть обозначение теста, который еще не готов к выполнению, атрибутом Ignore. Однако недостатком в этом случае является невозможность просто создать отчет по числу тестов, которые еще необходимо реализовать.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>  
  
 При написании нового класса исключения Assert наследование этого класса от базового класса UnitTestAssertException упрощает определение исключения как ошибки подтверждения, а не непредвиденного исключения, выдаваемого тестом или рабочим кодом.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>  
  
 Если необходимо, чтобы метод теста проверял, является ли исключение, возникающее в этом методе, на самом деле требуемым исключением, включите в метод теста атрибут ExpectedExceptionAttribute.  
  
## <a name="see-also"></a>См. также

<xref:Microsoft.VisualStudio.TestTools.UnitTesting>  
[Модульное тестирование кода](../test/unit-test-your-code.md)
