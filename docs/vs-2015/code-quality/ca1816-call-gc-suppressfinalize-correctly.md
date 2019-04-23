---
title: CA1816. Вызовите GC. SuppressFinalize правильно | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 50375390b3a09ec18fcccd45e4eaee7e9fe102e2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60094792"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816. Вызов GC.SuppressFinalize должен осуществляться правильно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Категория|Корпорация Майкрософт. Использование|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

- Метод, который представляет собой реализацию <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> не вызывает <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

- Метод, который не является реализацией <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> вызовы <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

- Вызывает метод <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> и передает что-то другое (Me в Visual Basic).

## <a name="rule-description"></a>Описание правила
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> Метод позволяет освободить ресурсы в любое время, прежде чем объект становится доступным для сборки мусора. Если <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> вызывается метод, он освобождает ресурсы объекта. Это исключает необходимость в завершении. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> следует вызывать <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> , сборщик мусора вызывает финализатор объекта.

 Чтобы предотвратить производные типы с финализаторами от необходимости повторно реализовать [System.IDisposable])<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->) и назовем ее, рекомендуется вызывать незапечатанных типов без использования методов завершения <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила:

 Если метод является реализацией <xref:System.IDisposable.Dispose%2A>, добавьте вызов <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 Если метод не является реализация <xref:System.IDisposable.Dispose%2A>, либо удалите вызов <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> или переместите его в тип <xref:System.IDisposable.Dispose%2A> реализации.

 Изменить все вызовы <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> для передачи (Me в Visual Basic).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Только подавить предупреждение из этого правила, если следует с помощью <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> управление временем существования других объектов. Не отключайте предупреждение из этого правила, если реализация <xref:System.IDisposable.Dispose%2A> не вызывает <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>. В этом случае сбой для подавления финализации снижает производительность и не дает положительных результатов.

## <a name="example"></a>Пример
 В следующем примере показано метод, который неправильно вызовы <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>Пример
 В следующем примере показано метод, который правильно вызовы <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2215: Методы Dispose должны вызывать метод dispose базового класса](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216: Высвобождаемые типы должны объявлять метод завершения](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>См. также
 [Шаблон ликвидации](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
