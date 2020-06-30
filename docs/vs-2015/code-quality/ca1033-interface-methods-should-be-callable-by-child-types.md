---
title: 'CA1033: методы интерфейса должны вызываться дочерними типами | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 18629f8d5c63b652d6539db10c6e6dba5d621c24
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542302"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033. Методы интерфейса должны быть доступны для вызова дочерними типами
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Незапечатанный тип, доступный для внешнего кода, предоставляет явную реализацию метода открытого интерфейса и не предоставляет доступный для внешнего кода альтернативный метод с тем же именем.

## <a name="rule-description"></a>Описание правила
 Рассмотрим базовый тип, который явно реализует открытый метод интерфейса. Тип, производный от базового типа, может обращаться к унаследованному методу интерфейса только через ссылку на текущий экземпляр ( `this` в C#), приведенный к интерфейсу. Если производный тип повторно реализует (явно) унаследованный метод интерфейса, базовая реализация больше не может быть доступна. Вызов через ссылку на текущий экземпляр вызовет производную реализацию. Это вызывает рекурсию и в конечном итоге переполнение стека.

 Это правило не сообщает о нарушении явной реализации, <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> Если предоставлен внешний видимый `Close()` метод или `System.IDisposable.Dispose(Boolean)` .

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, реализуйте новый метод, который предоставляет те же функциональные возможности и видимый для производных типов, или замените на неявную реализацию. Если критическое изменение допустимо, в качестве альтернативы можно сделать тип запечатанным.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если предоставлен внешний видимый метод, имеющий те же функциональные возможности, но отличающийся от имени явно реализованного метода.

## <a name="example"></a>Пример
 В следующем примере показан тип, `ViolatingBase` , который нарушает правило и тип, `FixedBase` который показывает исправление нарушения.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExplicitMethodImplementations/cs/FxCop.Design.ExplicitMethodImplementations.cs#1)]

## <a name="see-also"></a>См. также
 [Интерфейсы](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)
