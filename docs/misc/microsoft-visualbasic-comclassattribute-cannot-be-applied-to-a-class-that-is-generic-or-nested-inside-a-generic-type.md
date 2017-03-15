---
title: "Атрибут &quot;Microsoft.VisualBasic.ComClassAttribute&quot; не может применяться к универсальному классу или к классу, вложенному в универсальный тип. | Microsoft Docs"
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
  - "vbc31527"
  - "bc31527"
helpviewer_keywords: 
  - "BC31527"
ms.assetid: ea125bff-d020-4933-b277-6e24943eea88
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Атрибут &quot;Microsoft.VisualBasic.ComClassAttribute&quot; не может применяться к универсальному классу или к классу, вложенному в универсальный тип.
Класс объявляется с атрибутом <xref:Microsoft.VisualBasic.ComClassAttribute>, но он является универсальным или содержащимся в универсальном классе или структуре.  
  
 Чтобы соответствовать требованиям COM\-взаимодействия, класс .NET Framework должен отвечать следующим требованиям.  
  
-   Он должен быть `Public`, все его контейнеры должны быть `Public`, и он должен предоставлять по крайней мере один член `Public`.  
  
-   Он не должен быть *абстрактным*, то есть не должен быть объявлен с ключевым словом `MustInherit`.  
  
-   Он не должен быть универсальным или объявленным в типе универсального контейнера.  
  
 **Идентификатор ошибки:** BC31527  
  
### Исправление ошибки  
  
-   Измените объявление класса, чтобы он не был универсальным, и убедитесь, что содержащий его элемент не является универсальным.  
  
     \-или\-  
  
-   Если класс или содержащий его элемент должен быть универсальным, удалите атрибут <xref:Microsoft.VisualBasic.ComClassAttribute> из объявления класса. Вы не можете предоставлять его в COM.  
  
## См. также  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [COM\-взаимодействие](/dotnet/visual-basic/programming-guide/com-interop/index)   
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)