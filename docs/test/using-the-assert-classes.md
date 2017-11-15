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
ms.assetid: da1b7a0d-4f1d-4d50-a07e-7b3ff60053f9
caps.latest.revision: "27"
ms.author: douge
manager: douge
ms.openlocfilehash: 443c3fe0ece064993655895606ad8603b96f6286
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
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
 [Создание и запуск модульных тестов для существующего кода](http://msdn.microsoft.com/en-us/e8370b93-085b-41c9-8dec-655bd886f173)
