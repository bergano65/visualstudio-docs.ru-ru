---
title: CA2216. Высвобождаемые типы должны объявлять методы завершения
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1616e889b3892aa656692a3e5b0895d4b131b7f1
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231256"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216. Высвобождаемые типы должны объявлять методы завершения

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Тип, реализующий <xref:System.IDisposable?displayProperty=fullName>и имеющий поля, предлагающие использование неуправляемых ресурсов, не реализует метод завершения, как описано в. <xref:System.Object.Finalize%2A?displayProperty=fullName>

## <a name="rule-description"></a>Описание правила

Нарушение этого правила сообщается, если удаляемый тип содержит поля следующих типов:

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, реализуйте финализатор, который вызывает <xref:System.IDisposable.Dispose%2A> метод.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Можно отключить вывод предупреждения из этого правила, если тип не реализуется <xref:System.IDisposable> в целях освобождения неуправляемых ресурсов.

## <a name="example"></a>Пример

В следующем примере показан тип, нарушающий это правило.

[!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]

## <a name="related-rules"></a>Связанные правила

[CA2115 Вызовите GC. KeepAlive при использовании машинных ресурсов](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816: Вызовите GC. SuppressFinalize правильно](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA1049 Типы, владеющие собственными ресурсами, должны быть уничтожены](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>См. также

- <xref:System.IDisposable?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- [Шаблон ликвидации](/dotnet/standard/design-guidelines/dispose-pattern)