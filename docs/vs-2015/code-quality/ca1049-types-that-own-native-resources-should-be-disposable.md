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
ms.openlocfilehash: aaaf95346c51e2cb5cadb01a39e482bb508bc764
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668909"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: типы, которым принадлежат собственные ресурсы, должны быть высвобождаемыми
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип ссылается на поле <xref:System.IntPtr?displayProperty=fullName>, поле <xref:System.UIntPtr?displayProperty=fullName> или поле <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>, но не реализует <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Это правило предполагает, что поля <xref:System.IntPtr>, <xref:System.UIntPtr> и <xref:System.Runtime.InteropServices.HandleRef> хранят указатели на неуправляемые ресурсы. Типы, выделяющие неуправляемые ресурсы, должны реализовывать <xref:System.IDisposable>, чтобы позволить вызывающим объектам освобождать эти ресурсы по требованию и сократить время существования объектов, содержащих ресурсы.

 Рекомендуемый шаблон разработки для очистки неуправляемых ресурсов — предоставить как неявные, так и явные средства для высвобождения этих ресурсов с помощью метода <xref:System.Object.Finalize%2A?displayProperty=fullName> и метода <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> соответственно. Сборщик мусора вызывает метод <xref:System.Object.Finalize%2A> объекта в неопределенное время после того, как объект был определен как недостижимый. После вызова <xref:System.Object.Finalize%2A> для освобождения объекта требуется дополнительная сборка мусора. Метод <xref:System.IDisposable.Dispose%2A> позволяет вызывающему объекту явным образом освобождать ресурсы по запросу, более ранние, чем ресурсы будут освобождены, если оставить сборщик мусора. После очистки неуправляемых ресурсов <xref:System.IDisposable.Dispose%2A> должен вызвать метод <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>, чтобы сборщик мусора знал, что <xref:System.Object.Finalize%2A> больше не нужно вызывать. Это избавляет от необходимости дополнительной сборки мусора и сокращает время существования объекта.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, реализуйте <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила, если тип не ссылается на неуправляемый ресурс. В противном случае не отключайте предупреждение из этого правила, так как сбой реализации <xref:System.IDisposable> может привести к недоступности или невозможности использования неуправляемых ресурсов.

## <a name="example"></a>Пример
 В следующем примере показан тип, реализующий <xref:System.IDisposable> для очистки неуправляемого ресурса.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2115: вызывайте GC.KeepAlive при использовании машинных ресурсов](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: вызов GC.SuppressFinalize должен осуществляться правильно](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: высвобождаемые типы должны объявлять метод завершения](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>См. также раздел
  [Шаблон ликвидации](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
