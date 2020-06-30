---
title: 'CA1049: типы, которыми принадлежат собственные ресурсы, должны быть уничтожены | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 49c56b98e3be01675c2c21cd11c2961dd75f4877
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546813"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049. Типы, которым принадлежат собственные ресурсы, должны быть освобождаемыми
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип ссылается на <xref:System.IntPtr?displayProperty=fullName> поле, <xref:System.UIntPtr?displayProperty=fullName> поле или <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> поле, но не реализует <xref:System.IDisposable?displayProperty=fullName> .

## <a name="rule-description"></a>Описание правила
 Это правило предполагает, <xref:System.IntPtr> что <xref:System.UIntPtr> поля, и <xref:System.Runtime.InteropServices.HandleRef> хранят указатели на неуправляемые ресурсы. Типы, выделяющие неуправляемые ресурсы, должны реализовывать <xref:System.IDisposable> , чтобы позволить вызывающим объектам освобождать эти ресурсы по требованию и сократить время существования объектов, содержащих ресурсы.

 Рекомендуемым шаблоном разработки для очистки неуправляемых ресурсов является предоставление неявных и явных средств для высвобождения этих ресурсов с помощью <xref:System.Object.Finalize%2A?displayProperty=fullName> метода и <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> метода соответственно. Сборщик мусора вызывает <xref:System.Object.Finalize%2A> метод объекта в неопределенное время после того, как объект был определен как недостижимый. После <xref:System.Object.Finalize%2A> вызова для освобождения объекта требуется дополнительная сборка мусора. <xref:System.IDisposable.Dispose%2A>Метод позволяет вызывающему объекту явным образом освобождать ресурсы по запросу, более ранние, чем ресурсы будут освобождены, если оставить сборщик мусора. После очистки неуправляемых ресурсов <xref:System.IDisposable.Dispose%2A> следует вызвать <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> метод, чтобы сборщик мусора знал, что больше не нужно <xref:System.Object.Finalize%2A> вызывать. Это исключает необходимость в дополнительной сборке мусора и сокращает время существования объекта.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, реализуйте <xref:System.IDisposable> .

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила, если тип не ссылается на неуправляемый ресурс. В противном случае не отключайте предупреждение из этого правила, так как сбой реализации <xref:System.IDisposable> может привести к недоступности или невозможности использования неуправляемых ресурсов.

## <a name="example"></a>Пример
 В следующем примере показан тип, который реализует <xref:System.IDisposable> для очистки неуправляемого ресурса.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2115. Вызывайте GC.KeepAlive при использовании собственных ресурсов](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816. Вызов GC.SuppressFinalize должен осуществляться правильно](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216. Высвобождаемые типы должны объявлять методы завершения](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001. Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>См. также
  [Шаблон ликвидации](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
