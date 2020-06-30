---
title: 'CA1816: вызов GC. SuppressFinalize правильно | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 532478a8d6ed6b88347d196b4a74b6f19a38ef85
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546774"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816. Вызов GC.SuppressFinalize должен осуществляться правильно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|каллгксуппрессфинализекорректли|
|CheckId|CA1816|
|Категория|Microsoft. Использование|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

- Метод, который является реализацией, <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> не вызывает <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

- Метод, который не является реализацией <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> вызовов <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

- Метод вызывает <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> и передает нечто, отличное от this (я в Visual Basic).

## <a name="rule-description"></a>Описание правила
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>Метод позволяет пользователям освобождать ресурсы в любое время, прежде чем объект станет доступным для сборки мусора. При <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> вызове метода он освобождает ресурсы объекта. Это делает завершение ненужным. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>следует вызвать <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> , чтобы сборщик мусора не вызывал метод завершения объекта.

 Чтобы не допустить повторной реализации [System. IDisposable] в производных типах с методами завершения,<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->) и для вызова, незапечатанные типы без методов завершения должны по-прежнему вызывать <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, выполните следующие действия.

 Если метод является реализацией <xref:System.IDisposable.Dispose%2A> , добавьте вызов <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

 Если метод не является реализацией <xref:System.IDisposable.Dispose%2A> , удалите вызов <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> или переместите его в <xref:System.IDisposable.Dispose%2A> реализацию типа.

 Измените все вызовы на <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> , передав им (я в Visual Basic).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключать предупреждение из этого правила следует только в том случае, если используется <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> для управления временем существования других объектов. Не отключайте предупреждение из этого правила, если реализация не <xref:System.IDisposable.Dispose%2A> вызывает <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> . В этом случае не удается отключить завершение работы, что не дает никаких преимуществ.

## <a name="example"></a>Пример
 В следующем примере показан метод, который неправильно вызывает <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>Пример
 В следующем примере показан метод, который правильно вызывает <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2215. Метод Dispose должен вызывать базовый класс Dispose](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216. Высвобождаемые типы должны объявлять методы завершения](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>См. также
 [Шаблон ликвидации](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
