---
title: "Требуется ссылка на модуль &quot;&lt;имя_модуля&gt;&quot;, содержащий базовый класс &quot;&lt;имя_класса&gt;&quot; | Microsoft Docs"
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
  - "vbc30008"
  - "bc30008"
helpviewer_keywords: 
  - "BC30008"
ms.assetid: ec8de475-8a8b-4aa5-86c9-6fcc44dcec06
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Требуется ссылка на модуль &quot;&lt;имя_модуля&gt;&quot;, содержащий базовый класс &quot;&lt;имя_класса&gt;&quot;
Требуется ссылка на модуль "\<имя\_модуля\>", содержащий базовый класс "\<имя\_класса\>". Добавьте эту ссылку в проект.  
  
 Класс определяется в модуле, на который в проекте нет прямой ссылки. Компилятор [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] требует ссылки в целях устранения неоднозначности, если класс определен в нескольких модулях.  
  
 **Идентификатор ошибки:** BC30008  
  
### Исправление ошибки  
  
-   Включите в ссылки проекта имя модуля, на который нет ссылки.  
  
## См. также  
 [NIB. Создание ссылок на пространства имен и компоненты](http://msdn.microsoft.com/ru-ru/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Диагностика неработающих ссылок](../ide/troubleshooting-broken-references.md)