---
title: "Использование классов Assert | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Assert - классы"
  - "Assert - утверждения"
  - "модульные тесты, операторы Assert"
  - "модульные тесты, классы Assert"
ms.assetid: da1b7a0d-4f1d-4d50-a07e-7b3ff60053f9
caps.latest.revision: 27
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 27
---
# Использование классов Assert
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Классы Assert пространства имен UnitTestingFramework служат для проверки определенных функциональных возможностей.  Метод модульного теста использует код метода в коде разработки, но докладывает о корректности поведения кода только в том случае, если включены операторы Assert.  
  
## Типы классов Assert  
 Пространство имен <xref:Microsoft.VisualStudio.TestTools.UnitTesting> предоставляет несколько типов классов Assert.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>  
  
 В методе теста можно вызывать любое число методов класса Assert, таких как Assert.AreEqual\(\).  Класс Assert содержит много методов для выбора, и многие из этих методов имеют несколько перегрузок.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>  
  
 Класс CollectionAssert служит для сравнения коллекций объектов и проверки состояния одной или нескольких коллекций.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>  
  
 Класс StringAssert служит для сравнения строк.  Этот класс содержит различные полезные методы, такие как such as StringAssert.Contains, StringAssert.Matches и StringAssert.StartsWith.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>  
  
 Исключение AssertFailedException возникает в случае невыполнения теста.  Причиной невозможности выполнения теста может быть истечение времени ожидания, непредвиденное исключение или оператор Assert, создающий результат "Ошибка".  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>  
  
 Исключение AssertInconclusiveException возникает при каждом результате теста с неопределенным результатом.  Как правило, оператор Assert.Inconclusive добавляется к тесту, над которым еще ведется работа, для обозначения его неготовности к выполнению.  
  
> [!NOTE]
>  Альтернативным вариантом может быть обозначение теста, который еще не готов к выполнению, атрибутом Ignore.  Однако, недостатком в этом случае является невозможность простого создания отчета по числу тестов, которые еще необходимо реализовать.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>  
  
 При написании нового класса исключения Assert наследование этого класса от базового класса UnitTestAssertException упрощает выявление исключения как ошибки подтверждения, а не непредвиденного исключения, выдаваемого тестом или продуктивным кодом.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>  
  
 Если необходимо, чтобы метод теста проверял, что исключение, возникающее в этом методе, на самом деле является требуемым исключением, включите в метод теста атрибут ExpectedExceptionAttribute.  
  
## См. также  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>   
 [Создание и запуск модульных тестов для существующего кода](http://msdn.microsoft.com/ru-ru/e8370b93-085b-41c9-8dec-655bd886f173)