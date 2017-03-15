---
title: "Не удалось определить, является ли &quot;сборка&quot; многофайловой сборкой. Манифест сборки может быть поврежден. Предполагается, что сборка состоит из одного файла. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.unknownscatterstatusforcopy"
ms.assetid: be49d3f2-b091-488c-8579-e27ef09d9c80
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Не удалось определить, является ли &quot;сборка&quot; многофайловой сборкой. Манифест сборки может быть поврежден. Предполагается, что сборка состоит из одного файла.
Системе проектов не удалось считать сборку, на которую ссылается проект, поэтому система не может определить, является ли эта сборка состоящей из нескольких файлов. Поэтому сборка может быть неверно скопирована в выходную папку.  
  
 **Исправление ошибки**  
  
-   Переустановите [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(если сборка поставляется вместе с [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или .NET Framework\).  
  
     \-или\-  
  
-   Переустановите соответствующий элемент управления стороннего производителя.  
  
     Эта ошибка не помешает сборке проекта. Тем не менее возможна ошибка во время выполнения.  
  
## См. также  
 [Диагностика неработающих ссылок](../ide/troubleshooting-broken-references.md)   
 [NIB. Практическое руководство. Добавление и удаление ссылок с помощью диалогового окна "Добавление ссылок"](http://msdn.microsoft.com/ru-ru/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/ru-ru/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)