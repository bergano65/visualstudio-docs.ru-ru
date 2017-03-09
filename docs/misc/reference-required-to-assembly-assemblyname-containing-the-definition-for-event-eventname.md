---
title: "Требуется ссылка на сборку &quot;&lt;имя_сборки&gt;&quot;, содержащую определение события &quot;&lt;имя_события&gt;&quot; | Microsoft Docs"
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
  - "vbc30005"
  - "bc30005"
helpviewer_keywords: 
  - "BC30005"
ms.assetid: 843b0b2f-0f93-41c3-8727-13a2138e8140
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Требуется ссылка на сборку &quot;&lt;имя_сборки&gt;&quot;, содержащую определение события &quot;&lt;имя_события&gt;&quot;
Требуется ссылка на сборку "\<`assemblyname`\>", содержащую определение события "\<`eventname`\>". Добавьте эту ссылку в проект.  
  
 Событие определяется в библиотеке динамической компоновки \(DLL\) или в сборке, на которую в проекте нет прямой ссылки. Компилятор [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] требует ссылки в целях устранения неоднозначности, если событие определено в нескольких библиотеках DLL или сборках.  
  
 **Идентификатор ошибки:** BC30005  
  
### Исправление ошибки  
  
-   Включите в ссылки проекта имя библиотеки DLL или сборки, на которую нет ссылки.  
  
## См. также  
 [NIB. Создание ссылок на пространства имен и компоненты](http://msdn.microsoft.com/ru-ru/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Диагностика неработающих ссылок](../ide/troubleshooting-broken-references.md)