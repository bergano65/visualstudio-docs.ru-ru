---
title: Использование классов Assert | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Assert classes
- Assert statements
- unit tests, Assert statements
- unit tests, Assert classes
ms.assetid: da1b7a0d-4f1d-4d50-a07e-7b3ff60053f9
caps.latest.revision: 29
ms.author: gewarren
manager: douge
ms.openlocfilehash: 14bdea144a28e971d99ea8528b66e0bce1164035
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563672"
---
# <a name="using-the-assert-classes"></a>Использование классов Assert
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [использование классов Assert](https://docs.microsoft.com/visualstudio/test/using-the-assert-classes).  
  
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



