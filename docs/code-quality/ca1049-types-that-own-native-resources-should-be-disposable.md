---
title: "CA1049: типы, которым принадлежат собственные ресурсы, должны быть высвобождаемыми | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1049"
  - "TypesThatOwnNativeResourcesShouldBeDisposable"
helpviewer_keywords: 
  - "TypesThatOwnNativeResourcesShouldBeDisposable"
  - "CA1049"
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1049: типы, которым принадлежат собственные ресурсы, должны быть высвобождаемыми
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|  
|CheckId|CA1049|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Тип ссылается на поле <xref:System.IntPtr?displayProperty=fullName>, поле <xref:System.UIntPtr?displayProperty=fullName> или поле <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>, но не реализует <xref:System.IDisposable?displayProperty=fullName>.  
  
## Описание правила  
 Данное правило предполагает, что в полях <xref:System.IntPtr>, <xref:System.UIntPtr> и <xref:System.Runtime.InteropServices.HandleRef> хранятся указатели на неуправляемые ресурсы.  Типы, выделяющие неуправляемые ресурсы, должны реализовывать <xref:System.IDisposable>, чтобы вызывающие методы могли высвобождать эти ресурсы по требованию и сокращать время существования объектов, в которых хранятся ресурсы.  
  
 Рекомендуемым шаблоном разработки, используемым для освобождения неуправляемых ресурсов, является предоставление неявных и явных средств с помощью методов <xref:System.Object.Finalize%2A?displayProperty=fullName> и <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> соответственно.  Сборщик мусора вызывает метод <xref:System.Object.Finalize%2A> объекта через некоторое неопределенное время после того, как данный объект определен как больше недоступный.  После вызова метода <xref:System.Object.Finalize%2A> для освобождения объекта требуется дополнительная сборка мусора.  Метод <xref:System.IDisposable.Dispose%2A> позволяет вызывающим методам явным образом высвобождать ресурсы по требованию, причем это действие выполняется раньше, чем они были освобождены с помощью сборщика мусора.  После высвобождения неуправляемых ресурсов <xref:System.IDisposable.Dispose%2A> должен вызывать метод <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>, чтобы сообщить сборщику мусора об отсутствии необходимости вызова <xref:System.Object.Finalize%2A>, при этом сокращается время существования объекта и дополнительной сборки мусора не требуется.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, реализуйте <xref:System.IDisposable>.  
  
## Отключение предупреждений  
 Если тип не ссылается на неуправляемый ресурс, для данного правила можно отключить вывод предупреждений.  В противном случае не отключайте вывод предупреждений для данного правила, поскольку сбой реализации <xref:System.IDisposable> может привести к отсутствию доступа к неуправляемым ресурсам или к их недоиспользованию.  
  
## Пример  
 В следующем примере показан тип, реализующий <xref:System.IDisposable> для освобождения неуправляемого ресурса.  
  
 [!code-cs[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]  
  
## Связанные правила  
 [CA2115: вызывайте GC.KeepAlive при использовании собственных ресурсов](../Topic/CA2115:%20Call%20GC.KeepAlive%20when%20using%20native%20resources.md)  
  
 [CA1816: вызов GC.SuppressFinalize должен осуществляться правильно](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA2216: высвобождаемые типы должны объявлять метод завершения](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA1001: типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)  
  
## См. также  
 [Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md)   
 [Шаблон удаления](../Topic/Dispose%20Pattern.md)