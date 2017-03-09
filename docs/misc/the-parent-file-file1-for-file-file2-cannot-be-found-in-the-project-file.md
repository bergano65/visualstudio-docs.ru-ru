---
title: "The parent file, &#39;file1&#39;, for file &#39;file2&#39; cannot be found in the project file | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.projfile_missing_dependency"
ms.assetid: 1902c0b5-d09d-49b9-8f71-e325f7b9cfd7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The parent file, &#39;file1&#39;, for file &#39;file2&#39; cannot be found in the project file
Системе работы с проектами не удается найти узел, соответствующий файлу.  
  
 Зависимые файлы сохраняются в файле проекта путем добавления атрибута `DependentUpon` к узлу `<File>`.  Примеры.  
  
```  
<File  
    RelPath = "Form1.resx"  
    SubType = "Code"  
    BuildAction = "EmbeddedResource"  
    DependentUpon="Form1.vb"  
/>  
```  
  
 В иерархической структуре проекта под Form1.vb появится файл Form1.resx.  
  
 Эта ошибка часто возникает при редактировании файла проекта вручную.  
  
### Чтобы исправить эту ошибку  
  
-   Отредактируйте и обновите файл проекта.  
  
     Указанные файлы будут добавлены в проект, однако зависимость между ними учитываться не будет.  
  
## См. также  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/ru-ru/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)