---
title: "CA2215: методы Dispose должны вызывать такие же методы базового класса | Microsoft Docs"
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
  - "CA2215"
  - "DisposeMethodsShouldCallBaseClassDispose"
  - "Dispose methods should call base class dispose"
helpviewer_keywords: 
  - "DisposeMethodsShouldCallBaseClassDispose"
  - "CA2215"
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2215: методы Dispose должны вызывать такие же методы базового класса
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposeMethodsShouldCallBaseClassDispose|  
|CheckId|CA2215|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Тип, который реализует <xref:System.IDisposable?displayProperty=fullName>, наследует от типа, который также реализует <xref:System.IDisposable>.  Метод <xref:System.IDisposable.Dispose%2A> наследующего типа не вызывает метод <xref:System.IDisposable.Dispose%2A> родительского типа.  
  
## Описание правила  
 Если тип наследует от удаляемого типа, он должен вызвать метод <xref:System.IDisposable.Dispose%2A> базового типа из собственного метода <xref:System.IDisposable.Dispose%2A>.  Вызов метода базового типа Dispose гарантирует, что освобождаются все ресурсы, созданные базовым типом.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, вызовите метод `base`.<xref:System.IDisposable.Dispose%2A> из метода <xref:System.IDisposable.Dispose%2A>.  
  
## Отключение предупреждений  
 Можно игнорировать предупреждение этого правила, если вызов `base`.<xref:System.IDisposable.Dispose%2A> происходит на более глубоком уровне вызова по сравнению с уровнем проверки правила.  
  
## Пример  
 В следующем примере показан тип `TypeA`, который реализует объект <xref:System.IDisposable>.  
  
 [!CODE [FxCop.Usage.IDisposablePattern#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern#1)]  
  
## Пример  
 В следующем примере показан тип `TypeB`, который наследуется от типа `TypeA` и правильно вызывает его метод <xref:System.IDisposable.Dispose%2A>.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_1.vb)]  
  
## См. также  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Шаблон удаления](../Topic/Dispose%20Pattern.md)