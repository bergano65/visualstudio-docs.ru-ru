---
title: "Проект &quot;&lt;имя_проекта&gt;&quot; требует ссылку на версию &quot;&lt;номер_версии1&gt;&quot; сборки &quot;&lt;имя_сборки&gt;&quot;, но ссылается на версию &quot;&lt;номер_версии2&gt;&quot; сборки &quot;&lt;имя_сборки&gt;&quot; (ошибка Visual Basic) | Microsoft Docs"
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
  - "vbc32209"
  - "bc32209"
helpviewer_keywords: 
  - "BC32209"
ms.assetid: fe50736b-444f-4e40-8f80-9760ff13a153
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Проект &quot;&lt;имя_проекта&gt;&quot; требует ссылку на версию &quot;&lt;номер_версии1&gt;&quot; сборки &quot;&lt;имя_сборки&gt;&quot;, но ссылается на версию &quot;&lt;номер_версии2&gt;&quot; сборки &quot;&lt;имя_сборки&gt;&quot; (ошибка Visual Basic)
Проект делает косвенную ссылку на сборку, которая определена в каком\-либо месте, но проект также имеет прямую ссылку на более позднюю версию этой сборки.  
  
 Если компилятор разрешил вашему коду использовать косвенную ссылку, возможно, вы не сможете получить доступ к типам и программным элементам, которые были определены определен в более поздней версии, но не в более ранней версии.  
  
 **Идентификатор ошибки:** BC32209  
  
### Исправление ошибки  
  
-   Удалите косвенную ссылку на более раннюю версию сборки и используйте прямую ссылку на более позднюю версию.  
  
## См. также  
 [Сборки в среде CLR](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)   
 [NIB. Создание ссылок на пространства имен и компоненты](http://msdn.microsoft.com/ru-ru/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Управление ссылками в проекте](../ide/managing-references-in-a-project.md)   
 [NIB. Управление ссылками](http://msdn.microsoft.com/ru-ru/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB. Практическое руководство. Добавление и удаление ссылок с помощью диалогового окна "Добавление ссылки"](http://msdn.microsoft.com/ru-ru/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)