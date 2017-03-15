---
title: "Невозможно добавить файл &quot;файл&quot; в данный проект. &lt;причина&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_no_add_file"
ms.assetid: 8bd70556-596a-4e24-a71c-a340604ee93d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Невозможно добавить файл &quot;файл&quot; в данный проект. &lt;причина&gt;
Файл, считанный из файла VBPROJ или CSPROJ, нельзя добавить в проект. Причины.  
  
-   Недопустимое имя файла.  
  
-   Файл включен в путь. Например, существует относительный путь проекта File1\\File2.txt, но также имеется папка с относительным путем File1\\File2.txt.  
  
-   Элемент уже существует. Это происходит, когда файл указывается в файле проекта дважды.  
  
-   Ссылка уже существует. В системе проектов [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] и [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] есть ограничение, в соответствии с которым в каждом проекте может быть только одна ссылка с определенным именем. Это означает, например, что нельзя указать ссылку на файл VB как в папке A, так и в папке B проекта.  
  
 Наиболее вероятной причиной возникновения этой ошибки является изменение файла проекта вручную.  
  
 Файлы, для которых выводится это диагностическое сообщение, не добавляются в проект.  
  
## См. также  
 [Файлы проекта](/visual-cpp/ide/project-files)   
 [NIB. Управление элементами в проектах](http://msdn.microsoft.com/ru-ru/762e606b-7f44-4b66-97a1-e30a703654a0)