---
title: 'CA1816: вызов GC.SuppressFinalize должен осуществляться правильно'
ms.date: 06/30/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5c874aac5d84d45159ef7d169ab2749269fa0905
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174235"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: вызов GC.SuppressFinalize должен осуществляться правильно

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Категория|Корпорация Майкрософт. Использование|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Нарушение этого правила может быть вызвано:

- Метод, который представляет собой реализацию <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> и не вызывает <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Метод, который не является реализацией <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> и вызывает метод <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Метод, вызываемый <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> и передает что-то отличное от [this (C#)](/dotnet/csharp/language-reference/keywords/this) или [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="rule-description"></a>Описание правила

<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> Метод позволяет освободить ресурсы в любое время, прежде чем объект становится доступным для сборки мусора. Если <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> вызывается метод, он освобождает ресурсы объекта. Это исключает необходимость в завершении. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> следует вызывать <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> , сборщик мусора не вызывать метод завершения объекта.

Для предотвращения производным типам, используя методы завершения от необходимости повторно реализовать <xref:System.IDisposable> и назовем ее, рекомендуется вызывать незапечатанных типов без использования методов завершения <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила:

- Если метод является реализацией <xref:System.IDisposable.Dispose%2A>, добавьте вызов <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Если метод не является реализация <xref:System.IDisposable.Dispose%2A>, либо удалите вызов <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> или переместите его в тип <xref:System.IDisposable.Dispose%2A> реализации.

- Изменить все вызовы <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> для передачи [this (C#)](/dotnet/csharp/language-reference/keywords/this) или [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Только подавить предупреждение из этого правила, если вы используете намеренно <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> управление временем существования других объектов. Не отключайте предупреждение из этого правила, если реализация <xref:System.IDisposable.Dispose%2A> не вызывает <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>. В этом случае сбой для подавления финализации снижает производительность и не дает преимуществ.

## <a name="example-that-violates-ca1816"></a>Пример, который нарушает CA1816

Этот код показан метод, который вызывает <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>, но не проходит [this (C#)](/dotnet/csharp/language-reference/keywords/this) или [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me). Таким образом этот код нарушает правило CA1816.

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example-that-satisfies-ca1816"></a>Пример, который удовлетворяет CA1816

В этом примере показан метод, то правильно вызовы <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> , передав [this (C#)](/dotnet/csharp/language-reference/keywords/this) или [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>Связанные правила

- [CA2215: методы Dispose должны вызывать такие же методы базового класса](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)
- [CA2216: высвобождаемые типы должны объявлять метод завершения](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>См. также

- [Шаблон ликвидации](/dotnet/standard/design-guidelines/dispose-pattern)