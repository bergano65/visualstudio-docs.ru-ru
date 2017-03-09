---
title: "CA2216: высвобождаемые типы должны объявлять метод завершения | Microsoft Docs"
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
  - "DisposableTypesShouldDeclareFinalizer"
  - "CA2216"
helpviewer_keywords: 
  - "CA2216"
  - "DisposableTypesShouldDeclareFinalizer"
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2216: высвобождаемые типы должны объявлять метод завершения
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposableTypesShouldDeclareFinalizer|  
|CheckId|CA2216|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Тип, который реализует <xref:System.IDisposable?displayProperty=fullName> и имеет поля, предлагающие использование неуправляемых ресурсов, не реализует метод завершения, как описано в <xref:System.Object.Finalize%2A?displayProperty=fullName>.  
  
## Описание правила  
 Если высвобождаемый тип содержит поля, указанных ниже типов, выводится сообщение о нарушении данного правила.  
  
-   <xref:System.IntPtr?displayProperty=fullName>  
  
-   <xref:System.UIntPtr?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, реализуйте метод завершения, который вызывает метод <xref:System.IDisposable.Dispose%2A>.  
  
## Отключение предупреждений  
 Если тип не реализует <xref:System.IDisposable> для высвобождения неуправляемых ресурсов, для данного правила можно отключить вывод предупреждений.  
  
## Пример  
 В следующем примере показан тип, который нарушает данное правило.  
  
 [!code-cs[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]  
  
## Связанные правила  
 [CA2115: вызывайте GC.KeepAlive при использовании собственных ресурсов](../Topic/CA2115:%20Call%20GC.KeepAlive%20when%20using%20native%20resources.md)  
  
 [CA1816: вызов GC.SuppressFinalize должен осуществляться правильно](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA1049: типы, которым принадлежат собственные ресурсы, должны быть высвобождаемыми](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)  
  
## См. также  
 <xref:System.IDisposable?displayProperty=fullName>   
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 [Шаблон удаления](../Topic/Dispose%20Pattern.md)