---
title: "&quot;&lt;elementname&gt;&quot; ссылается на тип &quot;&lt;typename&gt;&quot; в проекте &quot;&lt;projectname&gt;&quot;, но тип &quot;&lt;typename&gt;&quot; не найден в проекте &quot;&lt;projectname&gt;&quot; | Microsoft Docs"
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
  - "vbc30960"
  - "bc30960"
helpviewer_keywords: 
  - "BC30960"
ms.assetid: 4ed4bff5-c670-46f6-8360-7287444d50e5
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;elementname&gt;&quot; ссылается на тип &quot;&lt;typename&gt;&quot; в проекте &quot;&lt;projectname&gt;&quot;, но тип &quot;&lt;typename&gt;&quot; не найден в проекте &quot;&lt;projectname&gt;&quot;
Выражение обращается к классу, структуре, модулю или интерфейсу, ссылающемуся на другой проект, но этот проект не содержит указанный тип.  
  
 Эта ошибка возникает, когда проект косвенно ссылается на другой проект в том же решении. Как правило, проект делает ссылку на сборку, которая ссылается на другой проект. Если сборка обращается к указанному типу в другом проекте, устанавливается косвенная ссылка на этот тип. Однако если данный тип отсутствует в другом проекте, возникает эта ошибка.  
  
 **Идентификатор ошибки:** BC30960  
  
### Исправление ошибки  
  
-   Если указанный тип больше нигде не определен, удалите или замените оператор, который пытается получить к нему доступ. Кроме того, может потребоваться внести то же изменение в сборку, предоставляющую косвенную ссылку на указанный тип.  
  
-   Если указанный тип определен где\-нибудь, внесите прямую ссылку на определяющий его проект или сборку.  
  
## См. также  
 [NIB. Создание ссылок на пространства имен и компоненты](http://msdn.microsoft.com/ru-ru/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Управление ссылками в проекте](../ide/managing-references-in-a-project.md)   
 [NIB. Управление ссылками](http://msdn.microsoft.com/ru-ru/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB. Практическое руководство. Добавление и удаление ссылок с помощью диалогового окна "Добавление ссылок"](http://msdn.microsoft.com/ru-ru/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)