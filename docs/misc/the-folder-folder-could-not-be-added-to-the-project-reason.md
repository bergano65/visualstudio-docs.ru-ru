---
title: "The folder &#39;folder&#39; could not be added to the project. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.projfile_no_add_folder"
ms.assetid: 3f6a5aa7-17cc-4e78-93b7-96e0970e111e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The folder &#39;folder&#39; could not be added to the project. &lt;reason&gt;
Папка, указанная в файле с расширением VBPROJ или CSPROJ, не может быть добавлена в проект.  Ниже указаны возможные причины.  
  
-   Недопустимое имя  
  
-   Часть пути совпадает с путем к файлу.  Например, при попытке включить в проект папку с относительным путем Папка1\\Папка2\\Папка3 и файл с относительным путем Папка1\\Папка2.  
  
-   Такой элемент уже существует.  Это происходит, когда папка указана в файле проекта дважды.  
  
 Эта ошибка часто возникает при редактировании файла проекта вручную.  
  
 **Чтобы исправить эту ошибку**  
  
-   Удалите поврежденный узел папки из файла проекта.  
  
     Папка \(вместе со всеми находящимися в ней файлами\), для которой выводится это диагностическое сообщение, не будет добавлена в проект.  
  
## См. также  
 [Файлы проекта](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/ru-ru/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)