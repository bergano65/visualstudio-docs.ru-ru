---
title: 'CA2216: удаляемые типы должны объявлять метод завершения | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 082afacba1ccf4c982e5ddceec37d2a1567efd7a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651651"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216: высвобождаемые типы должны объявлять метод завершения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип, реализующий <xref:System.IDisposable?displayProperty=fullName> и имеющий поля, предлагающие использование неуправляемых ресурсов, не реализует метод завершения, как описано в <xref:System.Object.Finalize%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Нарушение этого правила сообщается, если удаляемый тип содержит поля следующих типов:

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, реализуйте финализатор, который вызывает метод <xref:System.IDisposable.Dispose%2A>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если тип не реализует <xref:System.IDisposable> для освобождения неуправляемых ресурсов.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий это правило.

 [!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DisposeNoFinalize/cs/FxCop.Usage.DisposeNoFinalize.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2115: вызывайте GC.KeepAlive при использовании машинных ресурсов](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: вызов GC.SuppressFinalize должен осуществляться правильно](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA1049: типы, которым принадлежат собственные ресурсы, должны быть высвобождаемыми](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>См. также раздел
 <xref:System.IDisposable?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 [Шаблон ликвидации](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
