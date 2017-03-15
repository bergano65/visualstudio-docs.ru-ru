---
title: "Требуется ссылка на модуль &quot;&lt;имя_модуля&gt;&quot;, содержащий определение события &quot;&lt;имя_события&gt;&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30006"
  - "bc30006"
helpviewer_keywords: 
  - "BC30006"
ms.assetid: 7ab80acd-b47b-4920-bb15-6a3206b984e4
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Требуется ссылка на модуль &quot;&lt;имя_модуля&gt;&quot;, содержащий определение события &quot;&lt;имя_события&gt;&quot;
Требуется ссылка на модуль "\<`modulename`\>", содержащий определение события "\<`eventname`\>". Добавьте эту ссылку в проект.  
  
 Событие определяется в модуле, на который в проекте нет прямой ссылки. Компилятор [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] требует ссылки в целях устранения неоднозначности, если событие определено в нескольких модулях.  
  
 **Идентификатор ошибки:** BC30006  
  
### Исправление ошибки  
  
-   Включите в ссылки проекта имя модуля, на который нет ссылки.  
  
## См. также  
 [NIB. Ссылочные пространства имен и компоненты](http://msdn.microsoft.com/ru-ru/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Диагностика неработающих ссылок](../ide/troubleshooting-broken-references.md)