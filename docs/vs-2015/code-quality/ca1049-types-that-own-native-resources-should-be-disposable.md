---
title: CA1049. Типы, которым принадлежат собственные ресурсы, должны быть освобождаемыми | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 628a50a66c973020ff62d8041672901b2a578d31
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993117"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049. Типы, которым принадлежат собственные ресурсы, должны быть освобождаемыми
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Ссылается на тип <xref:System.IntPtr?displayProperty=fullName> поле <xref:System.UIntPtr?displayProperty=fullName> поля, или <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> поле, но не реализует <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Это правило предполагает, что <xref:System.IntPtr>, <xref:System.UIntPtr>, и <xref:System.Runtime.InteropServices.HandleRef> поля сохранения указателей на неуправляемые ресурсы. Типы, выделяющие неуправляемые ресурсы, должны реализовывать <xref:System.IDisposable> позволяет вызывающим объектам, чтобы освободить эти ресурсы по требованию и сокращать время существования объектов, занимающих ресурсы.

 Рекомендуемый шаблон для очистки неуправляемых ресурсов является неявным и явные означает, что для высвобождения этих ресурсов с помощью <xref:System.Object.Finalize%2A?displayProperty=fullName> метод и <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> метода, соответственно. Сборщик мусора вызывает <xref:System.Object.Finalize%2A> метод объекта в некоторых неопределенное время после объекта определяется как больше не доступен. После <xref:System.Object.Finalize%2A> вызывается, дополнительно требуется сбор мусора для освобождения объекта. <xref:System.IDisposable.Dispose%2A> Метод позволяет вызывающему объекту явно освобождать ресурсы по требованию, раньше, чем будет выпущен ресурсы, если сборщику мусора. После его очищает неуправляемые ресурсы, <xref:System.IDisposable.Dispose%2A> должны вызывать <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> метод, чтобы позволить следует помнить, что сборщик мусора <xref:System.Object.Finalize%2A> больше не нужно вызывать; это устраняет потребность в дополнительных при сборке мусора и сокращает время существования объекта.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, реализуйте <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если тип не ссылается неуправляемый ресурс. В противном случае не отключайте предупреждение из этого правила из-за сбоя для реализации <xref:System.IDisposable> может привести к неуправляемые ресурсы станут недоступными или простаивающие.

## <a name="example"></a>Пример
 В следующем примере показано тип, реализующий <xref:System.IDisposable> для очистки неуправляемого ресурса.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2115: Вызовите GC. KeepAlive при использовании машинных ресурсов](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: Вызовите GC. SuppressFinalize правильно](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: Высвобождаемые типы должны объявлять метод завершения](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>См. также
  [Шаблон ликвидации](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
