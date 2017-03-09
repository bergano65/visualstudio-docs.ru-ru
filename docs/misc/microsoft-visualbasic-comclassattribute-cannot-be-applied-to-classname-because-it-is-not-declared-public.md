---
title: "Атрибут &quot;Microsoft.VisualBasic.ComClassAttribute&quot; нельзя применить к классу &quot;&lt;имя_класса&gt;&quot;, поскольку он не объявлен как &quot;Public&quot;. | Microsoft Docs"
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
  - "bc32509"
  - "vbc32509"
helpviewer_keywords: 
  - "BC32509"
ms.assetid: ac46851f-53ab-4ce6-87b1-4c4d29508527
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Атрибут &quot;Microsoft.VisualBasic.ComClassAttribute&quot; нельзя применить к классу &quot;&lt;имя_класса&gt;&quot;, поскольку он не объявлен как &quot;Public&quot;.
Класс объявлен с атрибутом <xref:Microsoft.VisualBasic.ComClassAttribute>, но в его объявлении не указано `Public`.  
  
 Чтобы соответствовать требованиям COM\-взаимодействия, класс .NET Framework должен отвечать следующим требованиям.  
  
-   Он должен быть `Public`, все его контейнеры должны быть `Public`, и он должен предоставлять по крайней мере один член `Public`.  
  
-   Он не должен быть *абстрактным*, то есть не должен быть объявлен с ключевым словом `MustInherit`.  
  
-   Он не должен быть универсальным или объявленным в типе универсального контейнера.  
  
 **Идентификатор ошибки:** BC32509  
  
### Исправление ошибки  
  
-   Добавьте ключевое слово `Public` в объявление класса.  
  
     \-или\-  
  
-   Если класс или содержащий его элемент не может быть `Public`, удалите <xref:Microsoft.VisualBasic.ComClassAttribute> из объявления класса. Вы не можете предоставлять его в COM.  
  
## См. также  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [COM\-взаимодействие](/dotnet/visual-basic/programming-guide/com-interop/index)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)