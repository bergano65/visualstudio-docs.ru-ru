---
title: "Ошибка MSBuild MSB3021 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.Copy.Error"
helpviewer_keywords: 
  - "MSB3021"
ms.assetid: 8cb3a860-6916-4406-b5c7-b1106b44b92a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3021
**Не удалось скопировать файл "\<файл\>" в файл "\<файл\>". '  "\<ошибка\>"**  
  
 Задаче `Copy` не удается скопировать указанный файл.  
  
### Чтобы исправить эту ошибку  
  
-   Проверьте, не заблокирован \(используется\) ли целевой файл другим приложением.  Проверьте наличие разрешений на чтение исходного файла и запись в целевой файл в конечной папке.  Если путь целевого файла очень длинный, можно скопировать в другое место.  
  
## См. также  
 [Задача Copy](../msbuild/copy-task.md)   
 [Задачи](../msbuild/msbuild-tasks.md)