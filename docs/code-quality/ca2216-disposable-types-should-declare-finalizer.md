---
title: "CA2216: Высвобождаемые типы должны объявлять метод завершения | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 087df27916465b3ddba0b8e2c92bacf89dd33c1e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216: высвобождаемые типы должны объявлять метод завершения
|||  
|-|-|  
|TypeName|DisposableTypesShouldDeclareFinalizer|  
|CheckId|CA2216|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Тип, реализующий <xref:System.IDisposable?displayProperty=fullName>и имеет поля, предусматривающие использование неуправляемых ресурсов, не реализует метод завершения, в соответствии с <xref:System.Object.Finalize%2A?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Описание правила  
 Нарушение этого правила выводится в том случае, если удаляемого типа содержит поля из следующих типов:  
  
-   <xref:System.IntPtr?displayProperty=fullName>  
  
-   <xref:System.UIntPtr?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, реализуйте метод завершения, который вызывает ваш <xref:System.IDisposable.Dispose%2A> метод.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно подавить предупреждение из этого правила, если тип не реализует <xref:System.IDisposable> с целью освобождения неуправляемых ресурсов.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип, нарушающий это правило.  
  
 [!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2115: вызывайте GC.KeepAlive при использовании машинных ресурсов](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)  
  
 [CA1816: вызов GC.SuppressFinalize должен осуществляться правильно](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA1049: типы, которым принадлежат собственные ресурсы, должны быть высвобождаемыми](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)  
  
## <a name="see-also"></a>См. также  
 <xref:System.IDisposable?displayProperty=fullName>   
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 [Шаблон удаления](/dotnet/standard/design-guidelines/dispose-pattern)