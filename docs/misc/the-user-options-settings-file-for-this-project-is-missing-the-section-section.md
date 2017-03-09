---
title: "The user options settings file for this project is missing the &#39;section&#39; section | Microsoft Docs"
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
  - "vs.tasklisterror.peruserfile_sectionerr"
ms.assetid: 576070f5-76b6-46e4-8aba-83442521027f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The user options settings file for this project is missing the &#39;section&#39; section
В файле .vbproj.user или .csproj.user отсутствует узел "Build".  
  
 Раздел "Build" содержит параметры отладки.  Если этот раздел отсутствует, параметры отладки не будут загружены и примут значения по умолчанию.  
  
 Эта ошибка часто возникает при редактировании файла проекта вручную.  
  
 При закрытии проекта система работы с проектами автоматически обновит файл проекта для каждого пользователя.  
  
 Это сообщение является информационным.  
  
## См. также  
 [Файлы проекта](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/ru-ru/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)