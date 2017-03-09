---
title: "&lt;тип1&gt; &quot;&lt;имя_члена&gt;&quot; конфликтует с &lt;тип2&gt; &quot;&lt;имя_члена&gt;&quot; в базовом классе &lt;тип3&gt; &quot;&lt;имя_класса&gt;&quot; и должен быть объявлен как &quot;Shadows&quot; | Microsoft Docs"
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
  - "bc40004"
  - "vbc40004"
helpviewer_keywords: 
  - "BC40004"
ms.assetid: 24d10f31-3b3d-448c-b928-fc937e1f4a92
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;тип1&gt; &quot;&lt;имя_члена&gt;&quot; конфликтует с &lt;тип2&gt; &quot;&lt;имя_члена&gt;&quot; в базовом классе &lt;тип3&gt; &quot;&lt;имя_класса&gt;&quot; и должен быть объявлен как &quot;Shadows&quot;
Программный элемент объявлен с тем же именем, что и элемент, определенный в базовом классе. В этом случае элемент в данном классе должен затемнять элемент базового класса.  
  
 Это сообщение является предупреждением.`Shadows` подразумевается по умолчанию. Дополнительные сведения о скрытии предупреждений и обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC40004  
  
### Исправление ошибки  
  
-   Добавьте в объявление ключевое слово `Shadows` или измените имя объявляемого элемента.  
  
## См. также  
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Сокрытие в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)