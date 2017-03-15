---
title: "Член атрибута &quot;&lt;имя_члена&gt;&quot; не может быть целью назначения, так как он не объявлен как Public. | Microsoft Docs"
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
  - "vbc31511"
  - "bc31511"
helpviewer_keywords: 
  - "BC31511"
ms.assetid: f8c958f6-58a4-4aff-b8c3-f2e9481e8132
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Член атрибута &quot;&lt;имя_члена&gt;&quot; не может быть целью назначения, так как он не объявлен как Public.
Предпринята попытка назначить значение закрытому члену атрибута.  
  
 **Идентификатор ошибки:** BC31511  
  
### Исправление ошибки  
  
1.  Удалите назначение.  
  
2.  При использовании настраиваемых атрибутов собственной разработки измените модификатор доступа члена атрибута на `Public`.  
  
## См. также  
 [НЕ В СБОРКЕ. Атрибуты в Visual Basic](http://msdn.microsoft.com/ru-ru/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)