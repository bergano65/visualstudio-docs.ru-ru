---
title: "CA1033: Методы интерфейса должны быть доступны для вызова дочерним типам | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4694e1dbcbcf541b502edbe5f2520229ee33f4a6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: методы интерфейса должны быть доступны для вызова дочерним типам
|||  
|-|-|  
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|  
|CheckId|CA1033|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Незапечатанный тип, доступный для внешнего кода, предоставляет явную реализацию метода открытого интерфейса и не предоставляет доступный для внешнего кода альтернативный метод с тем же именем.  
  
## <a name="rule-description"></a>Описание правила  
 Рассмотрим базовый тип, который явно реализует открытый метод интерфейса. Тип, производный от базового типа можно обращаться из способ унаследованный интерфейс только ссылку на текущий экземпляр (`this` в C#), приводится к интерфейсу. Если производный тип повторно (явно реализует) способ унаследованный интерфейс, больше не возможен базовую реализацию. Вызов посредством ссылки на текущий экземпляр будет вызывать производной реализации; Это приводит к рекурсии и возможному переполнению стека.  
  
 Это правило не сообщает о нарушениях для явной реализацией <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> при Внешне видимый `Close()` или `System.IDisposable.Dispose(Boolean)` предоставляется метод.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, реализуйте новый метод, который предоставляет те же функциональные возможности и является видимым для производных типов или неявными реализации. Если допустима является критическим изменением, альтернативой является в запечатывании типа.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это безопасно подавить предупреждение из этого правила, если указан, имеет ту же функциональность, но имя, отличное от явно реализованный метод Внешне видимый метод.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип `ViolatingBase`, которое нарушает правило и тип `FixedBase`, демонстрирующий Устранение нарушения.  
  
 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы](/dotnet/csharp/programming-guide/interfaces/index)