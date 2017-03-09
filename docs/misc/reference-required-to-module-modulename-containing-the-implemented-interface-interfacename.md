---
title: "Требуется ссылка на модуль &quot;&lt;имя_модуля&gt;&quot;, содержащий реализованный интерфейс &quot;&lt;имя_интерфейса&gt;&quot; | Microsoft Docs"
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
  - "vbc30010"
  - "bc30010"
helpviewer_keywords: 
  - "BC30010"
ms.assetid: 57fe7e15-bf99-49d1-ba6c-bb7abeb615b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Требуется ссылка на модуль &quot;&lt;имя_модуля&gt;&quot;, содержащий реализованный интерфейс &quot;&lt;имя_интерфейса&gt;&quot;
Требуется ссылка на модуль "\<имя\_модуля\>", содержащий реализованный интерфейс "\<имя\_интерфейса\>". Добавьте эту ссылку в проект.  
  
 Интерфейс определяется в модуле, на который в проекте нет прямой ссылки. Компилятор [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] требует ссылку, чтобы исключить неоднозначность в случае, если событие определено в нескольких модулях.  
  
 **Идентификатор ошибки:** BC30010  
  
### Исправление ошибки  
  
-   Включите в ссылки проекта имя модуля, на который нет ссылки.  
  
## См. также  
 [NIB. Создание ссылок на пространства имен и компоненты](http://msdn.microsoft.com/ru-ru/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Диагностика неработающих ссылок](../ide/troubleshooting-broken-references.md)