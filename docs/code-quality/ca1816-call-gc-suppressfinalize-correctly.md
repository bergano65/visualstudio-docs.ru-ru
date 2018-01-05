---
title: "CA1816: Вызов сборки Мусора. SuppressFinalize правильно | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8d0287b570ed1ff5393ff0ff04b9e5d2252c29bf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: вызов GC.SuppressFinalize должен осуществляться правильно
|||  
|-|-|  
|TypeName|CallGCSuppressFinalizeCorrectly|  
|CheckId|CA1816|  
|Категория|Корпорация Майкрософт. Использование|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
  
-   Метод, который является реализацией <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> не вызывает <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
-   Метод, который не является реализация <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> вызовов <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
-   Вызывает метод <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> и передает что-либо другое (Me в Visual Basic).  
  
## <a name="rule-description"></a>Описание правила  
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> Метод позволяет пользователям освобождать ресурсы в любое время, прежде чем объект становится доступным для сборки мусора. Если <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> вызывается метод, он освобождает ресурсы объекта. Это исключает необходимость в завершении. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>следует вызвать <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> , сборщик мусора не должна вызывать метод завершения объекта.  
  
 Чтобы предотвратить необходимость повторной реализации производных типов с помощью методов завершения <xref:System.IDisposable> и вызывать его, рекомендуется вызывать незапечатанных типов без использования методов завершения <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение этого правила:  
  
 Если метод является реализацией <xref:System.IDisposable.Dispose%2A>, добавьте вызов <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 Если метод не является реализация <xref:System.IDisposable.Dispose%2A>, либо удалите вызов <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> или переместите его в тип <xref:System.IDisposable.Dispose%2A> реализации.  
  
 Изменить все вызовы <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> для передачи (Me в Visual Basic).  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Только отключайте предупреждение из этого правила, если следует с помощью <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> для управления временем жизни других объектов. Не отключайте предупреждение из этого правила, если реализация <xref:System.IDisposable.Dispose%2A> не вызывает <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>. В этом случае невозможность отключения завершения приводит к снижению производительности и не дает положительных результатов.  
  
## <a name="example"></a>Пример  
 В следующем примере показано метод, который неправильно вызовы <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]  
  
## <a name="example"></a>Пример  
 В следующем примере показано метод, который правильно вызовы <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2215: методы Dispose должны вызывать такие же методы базового класса](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA2216: высвобождаемые типы должны объявлять метод завершения](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
## <a name="see-also"></a>См. также  
 [Шаблон ликвидации](/dotnet/standard/design-guidelines/dispose-pattern)