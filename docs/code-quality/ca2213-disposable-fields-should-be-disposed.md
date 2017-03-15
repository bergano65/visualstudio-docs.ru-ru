---
title: "CA2213: следует высвобождать высвобождаемые поля | Microsoft Docs"
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
  - "DisposableFieldsShouldBeDisposed"
  - "CA2213"
helpviewer_keywords: 
  - "CA2213"
  - "DisposableFieldsShouldBeDisposed"
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2213: следует высвобождать высвобождаемые поля
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposableFieldsShouldBeDisposed|  
|CheckId|CA2213|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Тип, реализующий интерфейс <xref:System.IDisposable?displayProperty=fullName>, объявляет поля, принадлежащие типам, которые также реализуют интерфейс <xref:System.IDisposable>.  Метод <xref:System.IDisposable.Dispose%2A> поля не вызывается методом <xref:System.IDisposable.Dispose%2A> объявляющего типа.  
  
## Описание правила  
 Тип обеспечивает освобождение всех своих неуправляемых ресурсов за счет реализации интерфейса <xref:System.IDisposable>.  Данное правило проверяет, объявляет ли освобождаемый тип `T` поле `F`, которое является экземпляром освобождаемого типа `FT`.  Для каждого поля `F` правило пытается найти вызов метода `FT.Dispose`.  Правило выполняет поиск методов, вызываемых методом `T.Dispose`, и методов следующего уровня \(то есть методов, вызываемых методами, вызываемыми методом `FT.Dispose`\).  
  
## Устранение нарушений  
 Если в коде выполняется выделение и освобождение неуправляемых ресурсов, содержащихся в поле, то, чтобы устранить нарушение данного правила, вызовите метод <xref:System.IDisposable.Dispose%2A> для полей, принадлежащих типам, реализующим интерфейс <xref:System.IDisposable>.  
  
## Отключение предупреждений  
 Отключение предупреждений о нарушении данного правила безопасно в том случае, если в коде не требуется выполнять освобождение ресурсов, содержащихся в полях, или вызов метода <xref:System.IDisposable.Dispose%2A> осуществляется на более глубоком уровне дерева вызовов, чем тот, на котором выполняется проверка.  
  
## Пример  
 В следующем примере показан тип `TypeA`, который реализует интерфейс <xref:System.IDisposable> \(`FT` в предыдущем описании\).  
  
 [!CODE [FxCop.Usage.IDisposablePattern#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern#1)]  
  
## Пример  
 В следующем примере показан тип `TypeB`, который нарушает данное правило: он объявляет поле `aFieldOfADisposableType` \(`F` в предыдущем описании\) в качестве освобождаемого типа \(`TypeA`\) и не вызывает метод <xref:System.IDisposable.Dispose%2A> для этого поля.  `TypeB` соответствует `T` в предыдущем описании.  
  
 [!code-cs[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]  
  
## См. также  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Шаблон удаления](../Topic/Dispose%20Pattern.md)