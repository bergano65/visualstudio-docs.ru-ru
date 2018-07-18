---
title: 'CA1049: типы, которым принадлежат собственные ресурсы, должны быть высвобождаемыми'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 0f96f737274204018be3b30aaa4d85e07cc59f53
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900486"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: типы, которым принадлежат собственные ресурсы, должны быть высвобождаемыми
|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Ссылается на тип <xref:System.IntPtr?displayProperty=fullName> поля, <xref:System.UIntPtr?displayProperty=fullName> поля, или <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> поле, но не реализует <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Это правило предполагает, что <xref:System.IntPtr>, <xref:System.UIntPtr>, и <xref:System.Runtime.InteropServices.HandleRef> поля сохранения указателей на неуправляемые ресурсы. Типы, выделяющие неуправляемые ресурсы, должны реализовывать <xref:System.IDisposable> позволяет вызывающим освобождать эти ресурсы по требованию и сокращать время существования объектов, занимающих ресурсы.

 Рекомендуемый шаблон для очистки неуправляемых ресурсов является неявные и явные возможность освободить эти ресурсы с помощью <xref:System.Object.Finalize%2A?displayProperty=fullName> метод и <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> метода, соответственно. Сборщик мусора вызывает <xref:System.Object.Finalize%2A> метод объекта через некоторое неопределенное время после объект определен как больше не доступен. После <xref:System.Object.Finalize%2A> вызове дополнительный сбор мусора для освобождения объекта требуется. <xref:System.IDisposable.Dispose%2A> Метод позволяет вызывающему объекту явно освобождать ресурсы по требованию, более ранних, чем ресурсы будут освобождены Если оставить сборщика мусора. После его освобождает неуправляемые ресурсы, <xref:System.IDisposable.Dispose%2A> должен вызывать <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> метод, чтобы знать, что сборщик мусора <xref:System.Object.Finalize%2A> больше не должен вызываться; это устраняет потребность в дополнительных мусора и сокращает время существования объекта.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, реализуйте <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно безопасно подавить предупреждение из этого правила, если тип не ссылается неуправляемый ресурс. В противном случае не отключайте предупреждение из этого правила из-за сбоя для реализации <xref:System.IDisposable> может привести к неуправляемые ресурсы станут недоступными или простаивающие.

## <a name="example"></a>Пример
 В следующем примере показано тип, реализующий <xref:System.IDisposable> для очистки неуправляемых ресурсов.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>Связанные правила
 [CA2115: вызывайте GC.KeepAlive при использовании машинных ресурсов](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: вызов GC.SuppressFinalize должен осуществляться правильно](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: высвобождаемые типы должны объявлять метод завершения](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>См. также
 [Очистка неуправляемых ресурсов](/dotnet/standard/garbage-collection/unmanaged) [шаблон удаления](/dotnet/standard/design-guidelines/dispose-pattern)