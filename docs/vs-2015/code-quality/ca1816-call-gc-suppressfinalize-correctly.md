---
title: 'CA1816: Вызов сборки Мусора. SuppressFinalize правильно | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: e8c5123cc67dd6de273b9740a0a7dd4d7824eb10
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591916"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: вызов GC.SuppressFinalize должен осуществляться правильно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1816: вызов сборки Мусора. SuppressFinalize правильно](https://docs.microsoft.com/visualstudio/code-quality/ca1816-call-gc-suppressfinalize-correctly).

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Категория|Корпорация Майкрософт. Использование|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

-   Метод, который представляет собой реализацию <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> не вызывает <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

-   Метод, который не является реализацией <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> вызовы <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

-   Вызывает метод <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> и передает что-то другое (Me в Visual Basic).

## <a name="rule-description"></a>Описание правила
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> Метод позволяет освободить ресурсы в любое время, прежде чем объект становится доступным для сборки мусора. Если <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> вызывается метод, он освобождает ресурсы объекта. Это исключает необходимость в завершении. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> следует вызывать <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> , сборщик мусора вызывает финализатор объекта.

 Чтобы предотвратить необходимость повторной реализации [System.IDisposable] производным типам, используя методы завершения (<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->) и назовем ее, рекомендуется вызывать незапечатанных типов без использования методов завершения <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

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
 [CA2215: методы Dispose должны вызывать такие же методы базового класса](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216: высвобождаемые типы должны объявлять метод завершения](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>См. также
 [Шаблон ликвидации](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



