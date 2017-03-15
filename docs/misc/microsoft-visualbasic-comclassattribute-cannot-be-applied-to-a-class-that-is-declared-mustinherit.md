---
title: "Microsoft.VisualBasic.ComClassAttribute не может назначаться классу, который объявлен как MustInherit. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC32508"
  - "vbc32508"
helpviewer_keywords: 
  - "BC32508"
ms.assetid: c8af606d-f448-4703-98df-e594fd511f92
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Microsoft.VisualBasic.ComClassAttribute не может назначаться классу, который объявлен как MustInherit.
Класс объявлен с атрибутом <xref:Microsoft.VisualBasic.ComClassAttribute>, но в его объявлении есть ключевое слово `MustInherit`.  
  
 Чтобы соответствовать требованиям COM\-взаимодействия, класс .NET Framework должен отвечать следующим требованиям.  
  
-   Он должен быть `Public`, все его контейнеры должны быть `Public`, и он должен предоставлять по крайней мере один член `Public`.  
  
-   Он не должен быть *abstract*, то есть не должен быть объявлен с ключевым словом `MustInherit`.  
  
-   Он не должен быть универсальным или объявлен в типе универсального контейнера.  
  
 **Идентификатор ошибки:** BC32508  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `MustInherit` из объявления класса.  
  
     \-или\-  
  
-   Если класс или его элемент должен быть универсальным, удалите атрибут <xref:Microsoft.VisualBasic.ComClassAttribute> из объявления класса. Вы не можете предоставлять его в COM.  
  
## См. также  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [COM\-взаимодействие](/dotnet/visual-basic/programming-guide/com-interop/index)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)