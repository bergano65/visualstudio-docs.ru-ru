---
title: CA2216. Высвобождаемые типы должны объявлять методы завершения
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f53f91a6a4775fb17e273fb87c4c669f74ad45e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826001"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216. Высвобождаемые типы должны объявлять методы завершения

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Тип, реализующий <xref:System.IDisposable?displayProperty=fullName>и имеет поля, предусматривающие использование неуправляемых ресурсов, не реализует метод завершения, как описано в <xref:System.Object.Finalize%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила

Нарушение этого правила выводится в том случае, если уничтожаемого типа содержит поля из следующих типов:

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, реализуйте метод завершения, который вызывает ваш <xref:System.IDisposable.Dispose%2A> метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Это безопасно подавить предупреждение из этого правила, если тип не реализует <xref:System.IDisposable> для высвобождения неуправляемых ресурсов.

## <a name="example"></a>Пример

В следующем примере тип, который нарушает это правило.

[!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]

## <a name="related-rules"></a>Связанные правила

[CA2115: Вызовите GC. KeepAlive при использовании машинных ресурсов](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816: Вызовите GC. SuppressFinalize правильно](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA1049: Типы, которым принадлежат собственные ресурсы, должны быть освобождаемыми](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>См. также

- <xref:System.IDisposable?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- [Шаблон ликвидации](/dotnet/standard/design-guidelines/dispose-pattern)