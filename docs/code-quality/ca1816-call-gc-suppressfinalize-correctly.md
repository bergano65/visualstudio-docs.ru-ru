---
title: "CA1816: вызов GC.SuppressFinalize должен осуществляться правильно | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1816"
  - "DisposeMethodsShouldCallSuppressFinalize"
helpviewer_keywords: 
  - "CA1816"
  - "DisposeMethodsShouldCallSuppressFinalize"
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1816: вызов GC.SuppressFinalize должен осуществляться правильно
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallGCSuppressFinalizeCorrectly|  
|CheckId|CA1816|  
|Категория|Microsoft.  Использование|  
|Критическое изменение|Не критическое|  
  
## Причина  
  
-   Метод, являющийся реализацией <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>, не вызывает <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
-   Метод, не являющийся реализацией <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>, вызывает <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
-   Метод вызывает <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> и передает значение, отличное от данного \("Me" в Visual Basic\).  
  
## Описание правила  
 Метод <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> позволяет пользователям освобождать ресурсы в любое время, прежде чем объект становится доступным для сборки мусора.  Если вызвать метод <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>, ресурсы объекта будут очищены.  Это делает финализацию ненужной.  <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> должен вызвать <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>, чтобы сборщик мусора не вызывал метод завершения объекта.  
  
 Чтобы исключить необходимость повторной реализации [System.IDisposable](assetId:///System.IDisposable?qualifyHint=True&autoUpgrade=False) производными типами с методами завершения, а также для его вызова, незапечатанные типы без методов завершения должны по\-прежнему вызывать <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, выполните следующие действия  
  
 Если метод является реализацией <xref:System.IDisposable.Dispose%2A>, добавьте вызов <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 Если метод не является реализацией <xref:System.IDisposable.Dispose%2A>, удалите вызов <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> или переместите его в реализацию типа <xref:System.IDisposable.Dispose%2A>.  
  
 Измените все вызовы <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> для передачи этого \(Me в Visual Basic\).  
  
## Отключение предупреждений  
 Отключать вывод предупреждения по этому правилу следует только в том случае, если рассматривается возможность использования <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> для управления временем жизни других объектов.  Не отключайте вывод предупреждений по этому правилу, если реализация <xref:System.IDisposable.Dispose%2A> не вызывает <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  В этом случае, невозможность отключения завершения отрицательно сказывается на производительности и не дает положительных результатов.  
  
## Пример  
 В следующем примере показан метод, неправильно вызывающий <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
 [!code-cs[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]  
  
## Пример  
 В следующем примере показан метод, правильно вызывающий <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 [!CODE [FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1)]  
  
## Связанные правила  
 [CA2215: методы Dispose должны вызывать такие же методы базового класса](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA2216: высвобождаемые типы должны объявлять метод завершения](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
## См. также  
 [Шаблон удаления](../Topic/Dispose%20Pattern.md)