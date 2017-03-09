---
title: "Invalid assembly strong name or name not specified | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.invalid_strong_name"
ms.assetid: cb02b69d-09a9-478f-914c-fbdc420e973d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Invalid assembly strong name or name not specified
В объектной модели системы работы с проектами оказалось пустым свойство проекта, позволяющее задавать имя ключа или контейнер ключа для проектов, по которым должны строиться сборки со строгими именами \(подписанные сборки\).  При возникновении этой ошибки процесс построения завершается неудачей.  
  
### Чтобы исправить эту ошибку  
  
1.  Убедитесь, что в коде заданы либо имя контейнера ключа, либо файл ключа.  
  
## См. также  
 [Создание и использование сборок со строгими именами](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)