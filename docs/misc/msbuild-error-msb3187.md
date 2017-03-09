---
title: "Ошибка MSBuild MSB3187 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.PlatformMismatch"
helpviewer_keywords: 
  - "MSB3187"
ms.assetid: c5e93c14-b099-4176-bf1b-dbecc47fb3fd
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3187
**MSB3187: Сборка\>' сборки '\<, на которую нацелен другой процессор запуском приложения.**  
  
 Это предупреждение появляется, когда задана нейтральная \(MSIL\) целевая платформа приложения \(архитектура процессора\), а указанная в ссылке сборка не является нейтральной, или когда архитектура приложения не является нейтральной, а зависимость нейтральная.  Если для обеих не задана нейтральная платформа, то их архитектуры должны совпадать.  Кроме того, архитектура приложения и архитектура сборки точки входа всегда должны совпадать.  
  
### Чтобы исправить эту ошибку  
  
-   Убедитесь, что целевая платформа приложения \(архитектура процессора\) совпадает со всеми указанными в ссылках сборками и архитектурой сборки точки входа.  
  
## См. также  
 [Диалоговое окно "Дополнительные параметры компилятора" \(Visual Basic\)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)   
 [Страница "Построение" в конструкторе проектов \(C\#\)](../ide/reference/build-page-project-designer-csharp.md)