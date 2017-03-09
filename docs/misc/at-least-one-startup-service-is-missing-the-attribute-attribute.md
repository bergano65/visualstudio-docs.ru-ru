---
title: "At least one startup service is missing the &#39;attribute&#39; attribute | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_missing_ss_attrib"
ms.assetid: 987c42dc-4394-4b07-b7fa-a8e7afc6fdfb
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one startup service is missing the &#39;attribute&#39; attribute
Службе запуска требуется атрибут "ID", который не может быть найден у элемента `<Service>`.  Примеры.  
  
```  
<Service ID="{0000-0000-0000-00000000-000000000000}"/>  
```  
  
 Это означает, что файл проекта поврежден.  
  
 Эта ошибка часто возникает при редактировании файла проекта вручную.  
  
 **Чтобы исправить эту ошибку**  
  
-   Сохраните файл проекта.  
  
     Поврежденный раздел не будет сохранен и эта ошибка не произойдет в следующий раз, когда проект будет открыт.  
  
## См. также  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/ru-ru/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)