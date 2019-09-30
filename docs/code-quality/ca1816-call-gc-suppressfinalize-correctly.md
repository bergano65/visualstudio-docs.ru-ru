---
title: CA1816. Вызов GC.SuppressFinalize должен осуществляться правильно
ms.date: 06/30/2018
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3fdd20df37586e50b5236872f1d84de48d08c87a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233532"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816. Вызов GC.SuppressFinalize должен осуществляться правильно

|||
|-|-|
|TypeName|каллгксуппрессфинализекорректли|
|CheckId|CA1816|
|Категория|NNTP. Использование|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Нарушения этого правила могут быть вызваны следующими причинами.

- Метод, который является реализацией <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> и не вызывает. <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>

- Метод, который не является реализацией <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> и вызывает. <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>

- Метод, который вызывает <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> и передает нечто, отличное от [thisC#()](/dotnet/csharp/language-reference/keywords/this) или [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="rule-description"></a>Описание правила

<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> Метод позволяет пользователям освобождать ресурсы в любое время, прежде чем объект станет доступным для сборки мусора. При вызове <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> метода он освобождает ресурсы объекта. Это делает завершение ненужным. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>должен вызывать <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> , чтобы сборщик мусора не вызывал метод завершения объекта.

Чтобы не допустить повторной реализации <xref:System.IDisposable> и вызова для производных типов с помощью методов завершения, незапечатанные типы не должны вызывать. <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, выполните следующие действия.

- Если метод является реализацией <xref:System.IDisposable.Dispose%2A>, добавьте <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>вызов.

- Если метод не является реализацией <xref:System.IDisposable.Dispose%2A>, удалите <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> вызов или переместите <xref:System.IDisposable.Dispose%2A> его в реализацию типа.

- Измените все вызовы <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> на, чтобы передать [thisC#()](/dotnet/csharp/language-reference/keywords/this) или [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Отключать предупреждение из этого правила следует только в том случае, если <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> вы намеренно используете для управления временем существования других объектов. Не отключайте предупреждение из этого правила, если реализация <xref:System.IDisposable.Dispose%2A> не вызывает <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>. В этом случае не удается отключить завершение работы, что не дает никаких преимуществ.

## <a name="example-that-violates-ca1816"></a>Пример, нарушающий CA1816

Этот код показывает метод, который вызывает <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>, но не передает [this (C#)](/dotnet/csharp/language-reference/keywords/this) или [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me). В результате этот код нарушает правило CA1816.

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example-that-satisfies-ca1816"></a>Пример, удовлетворяющий CA1816

В этом примере показан метод, который правильно <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> вызывается путем передачи [этогоC#()](/dotnet/csharp/language-reference/keywords/this) или [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>Связанные правила

- [CA2215 Методы Dispose должны вызывать базовый класс Dispose](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)
- [CA2216: Удаляемые типы должны объявлять метод завершения](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>См. также

- [Шаблон удаления](/dotnet/standard/design-guidelines/dispose-pattern)