---
title: 'CA1033: методы интерфейса должны быть доступны для вызова дочерним типам'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c41b19d9d4a82e25223a9cf7b04034b37c3f45fb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
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