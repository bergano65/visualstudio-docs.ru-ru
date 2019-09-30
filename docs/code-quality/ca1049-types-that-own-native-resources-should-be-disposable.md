---
title: CA1049. Типы, которым принадлежат собственные ресурсы, должны быть освобождаемыми
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- cplusplus
ms.openlocfilehash: ef7b72eade7ea8e4486d5c317c06026bb4d0b95f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235743"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049. Типы, которым принадлежат собственные ресурсы, должны быть освобождаемыми

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Тип ссылается <xref:System.IntPtr?displayProperty=fullName> на поле <xref:System.UIntPtr?displayProperty=fullName> , поле или <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> поле, но не реализует <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила

Это правило предполагает, <xref:System.IntPtr>что <xref:System.UIntPtr>поля, <xref:System.Runtime.InteropServices.HandleRef> и хранят указатели на неуправляемые ресурсы. Типы, выделяющие неуправляемые ресурсы <xref:System.IDisposable> , должны реализовывать, чтобы позволить вызывающим объектам освобождать эти ресурсы по требованию и сократить время существования объектов, содержащих ресурсы.

Рекомендуемым шаблоном разработки для очистки неуправляемых ресурсов является предоставление неявных и явных средств для высвобождения этих ресурсов с помощью <xref:System.Object.Finalize%2A?displayProperty=fullName> метода <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> и метода соответственно. Сборщик мусора вызывает <xref:System.Object.Finalize%2A> метод объекта в неопределенное время после того, как объект был определен как недостижимый. После <xref:System.Object.Finalize%2A> вызова для освобождения объекта требуется дополнительная сборка мусора. <xref:System.IDisposable.Dispose%2A> Метод позволяет вызывающему объекту явным образом освобождать ресурсы по запросу, более ранние, чем ресурсы будут освобождены, если оставить сборщик мусора. После очистки неуправляемых ресурсов <xref:System.IDisposable.Dispose%2A> следует <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> вызвать метод, чтобы сборщик мусора знал, что <xref:System.Object.Finalize%2A> больше не нужно вызывать. Это исключает необходимость в дополнительной сборке мусора и сокращает время существования объекта.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, реализуйте <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Можно отключить вывод предупреждения из этого правила, если тип не ссылается на неуправляемый ресурс. В противном случае не отключайте предупреждение из этого правила, так <xref:System.IDisposable> как сбой реализации может привести к недоступности или невозможности использования неуправляемых ресурсов.

## <a name="example"></a>Пример
В следующем примере показан тип, который реализует <xref:System.IDisposable> для очистки неуправляемого ресурса.

[!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
[!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>Связанные правила
[CA2115 Вызовите GC. KeepAlive при использовании машинных ресурсов](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816: Вызовите GC. SuppressFinalize правильно](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA2216: Удаляемые типы должны объявлять метод завершения](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

[CA1001: типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>См. также

- [Очистка неуправляемых ресурсов](/dotnet/standard/garbage-collection/unmanaged)
- [Шаблон ликвидации](/dotnet/standard/design-guidelines/dispose-pattern)