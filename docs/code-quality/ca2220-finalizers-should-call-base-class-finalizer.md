---
title: "CA2220: методы завершения должны вызывать метод завершения базового класса | Microsoft Docs"
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
  - "CA2220"
  - "FinalizersShouldCallBaseClassFinalizer"
helpviewer_keywords: 
  - "CA2220"
  - "FinalizersShouldCallBaseClassFinalizer"
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2220: методы завершения должны вызывать метод завершения базового класса
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|FinalizersShouldCallBaseClassFinalizer|  
|CheckId|CA2220|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Тип, переопределяющий <xref:System.Object.Finalize%2A?displayProperty=fullName>, не вызывает метод <xref:System.Object.Finalize%2A> в своем базовом классе.  
  
## Описание правила  
 Финализация должна распространятся посредством иерархии наследования.  Для этого типы должны вызывать метод <xref:System.Object.Finalize%2A> своего базового класса из своего собственного метода <xref:System.Object.Finalize%2A>.  Компилятор C\# автоматически добавляет вызов финализатора базового класса.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, вызовите метод <xref:System.Object.Finalize%2A> базового класса из метода <xref:System.Object.Finalize%2A>.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  Некоторые компиляторы, работающие со средой CLR, вставляют вызов финализатора базового типа в язык MSIL.  При возникновении предупреждения этого правила компилятор не вставляет вызов, поэтому нужно добавить его в код.  
  
## Пример  
 В следующем примере на языке Visual Basic показан тип `TypeB`, правильно вызывающий метод <xref:System.Object.Finalize%2A> в своем базовом классе.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]  
  
## См. также  
 [Шаблон удаления](../Topic/Dispose%20Pattern.md)