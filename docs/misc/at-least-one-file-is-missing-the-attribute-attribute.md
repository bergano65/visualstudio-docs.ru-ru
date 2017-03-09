---
title: "At least one file is missing the &#39;attribute&#39; attribute | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_missing_file_attrib"
ms.assetid: 2627974b-c9cd-4d85-9af4-dd3811214ea4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one file is missing the &#39;attribute&#39; attribute
В узле файла, указанный в файле с расширением VBPROJ или CSPROJ, отсутствуют определенные атрибуты, необходимые системе работы с проектами.  В настоящее время единственным таким атрибутом является `RelPath`, который определяет, где располагается файл внутри папки проекта.  
  
 Эта ошибка часто возникает при редактировании файла проекта вручную.  
  
 **Чтобы исправить эту ошибку**  
  
-   Удалите поврежденный узел файла из файла проекта.  Если файл все ещё находится на диске, можно переключиться в режим **Показать все файлы** \(нажав соответствующую кнопку в панели инструментов обозревателя решений\), затем щелкнуть правой кнопкой мыши данный файл и выбрать команду **Включить в проект**.  
  
     Файл, для которого отсутствует атрибут `RelPath`, не будет добавлен в проект.  
  
## См. также  
 [Файлы проекта](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/ru-ru/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)