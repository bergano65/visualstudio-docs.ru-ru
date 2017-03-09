---
title: "At least one folder is missing the &#39;attribute&#39; attribute | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_missing_fold_attrib"
ms.assetid: 3a0498a9-df61-47d8-a228-f88f4f138df8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one folder is missing the &#39;attribute&#39; attribute
В узле папки, указанной в файле с расширением VBPROJ или CSPROJ, отсутствуют определенные атрибуты, необходимые системе работы с проектами.  В настоящее время единственным таким атрибутом является **RelPath**, который определяет, где располагается данная папка внутри папки проекта.  
  
 Эта ошибка часто возникает при редактировании файла проекта вручную.  
  
 **Чтобы исправить эту ошибку**  
  
-   Удалите поврежденный узел папки из файла проекта.  Если папка все ещё находится на диске, можно переключиться в режим "Показать все файлы" \(нажав соответствующую кнопку в панели инструментов обозревателя решений\), затем щелкнуть правой кнопкой мыши эту папку и выбрать команду **Включить в проект**.  
  
     Папка, для которой отсутствует атрибут, не будет добавлена в проект.  
  
## См. также  
 [Файлы проекта](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/ru-ru/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)