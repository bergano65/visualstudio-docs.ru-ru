---
title: "Microsoft.VisualBasic.ComClassAttribute не может использоваться для &quot;&lt;имя_класса1&gt;&quot;, т.&#160;к. его контейнер &quot;&lt;имя_класса2&gt;&quot; не объявлен как &quot;Public&quot; | Microsoft Docs"
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
  - "vbc32504"
  - "bc32504"
helpviewer_keywords: 
  - "BC32504"
ms.assetid: 4138b639-88d6-4b51-afcd-c92a1be36f1c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Microsoft.VisualBasic.ComClassAttribute не может использоваться для &quot;&lt;имя_класса1&gt;&quot;, т.&#160;к. его контейнер &quot;&lt;имя_класса2&gt;&quot; не объявлен как &quot;Public&quot;
Класс, использующий блок атрибута `COMClassAttribute`, объявлен внутри класса, который не является `Public`. Если класс должен быть предоставлен как COM\-объект, вся содержащая его иерархия должна быть объявлена с уровнем доступа `Public`.  
  
 **Идентификатор ошибки:** BC32504  
  
### Исправление ошибки  
  
-   Объявите все содержащие классы как `Public` или удалите блок атрибута `COMClassAttribute`.  
  
## См. также  
 [НЕ В СБОРКЕ. Атрибуты, используемые в Visual Basic](http://msdn.microsoft.com/ru-ru/22231318-8a40-49af-9245-e0aab723563b)   
 [НЕ В СБОРКЕ. Применение атрибутов](http://msdn.microsoft.com/ru-ru/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Класс ComClassAttribute](http://msdn.microsoft.com/ru-ru/5c2f0835-9210-47dc-bc59-5c1769953574)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)