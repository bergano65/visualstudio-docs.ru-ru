---
title: "Не удалось определить, является ли &quot;сборка&quot; многофайловой сборкой. Манифест сборки может быть поврежден. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannotfindscatterinfo"
ms.assetid: 2d4af6ef-c2f8-4764-af8b-580d433bfbc9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Не удалось определить, является ли &quot;сборка&quot; многофайловой сборкой. Манифест сборки может быть поврежден.
Системе проектов не удалось прочитать сборку, на которую проект ссылается таким образом, что системе проектов не удается определить, на какие файлы ссылается сборка.  
  
 **Исправление ошибки**  
  
-   Переустановите Visual Studio \(если сборка поставляется вместе с [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\).  
  
     \-или\-  
  
-   Переустановите соответствующий элемент управления стороннего производителя.  
  
     Эта ошибка не помешает сборке проекта. Тем не менее возможна ошибка во время выполнения.  
  
## См. также  
 [Диагностика неработающих ссылок](../ide/troubleshooting-broken-references.md)   
 [NIB. Практическое руководство. Добавление и удаление ссылок с помощью диалогового окна "Добавление ссылок"](http://msdn.microsoft.com/ru-ru/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/ru-ru/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)