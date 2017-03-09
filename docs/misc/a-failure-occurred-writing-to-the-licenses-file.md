---
title: "A failure occurred writing to the licenses file | Microsoft Docs"
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
  - "vs.tasklisterror.fail_writing_licenses_file"
ms.assetid: 7ea1e2ac-fc94-4d53-8ce9-2ae31bcba85d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# A failure occurred writing to the licenses file
Системе работы с проектами не удалось записать преобразованный файл.  В процессе подготовки лицензий система работы с проектами преобразует текстовые LICX\-файлы в двоичные файлы лицензий, которые распознаются системой лицензирования [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Возможные причины этой ошибки включают: отсутствие свободного места на диске устройства или превышение предела MAX\_PATH для имен файлов.  
  
 **Чтобы исправить эту ошибку**  
  
-   Переместите проект в другую папку с более коротким абсолютным путем или сократите имя выходного файла.  
  
     При возникновении этой ошибки процесс построения завершается неудачей.  
  
## См. также  
 [How to: License Components and Controls](../Topic/How%20to:%20License%20Components%20and%20Controls.md)