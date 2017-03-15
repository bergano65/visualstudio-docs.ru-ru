---
title: "Could not instantiate the licenses processor | Microsoft Docs"
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
  - "vs.tasklisterror.no_licx_generator"
ms.assetid: 9e95d590-f41f-4cfa-bc73-fadeacfdb879
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not instantiate the licenses processor
Не удается создать экземпляр средства, которое используется для преобразования LICX\-файлов в двоичные файлы ресурсов.  
  
 В процессе компиляции система работы с проектами преобразует текстовый LICX\-файл в двоичный файл ресурсов, который предоставляет поддержку для лицензирования элементов управления .NET.  Двоичный файл ресурсов будет затем внедрен в выходной файл проекта.  
  
 При возникновении этой ошибки процесс построения завершается неудачей.  
  
 LICX\-файл автоматически создается или обновляется конструктором Windows Forms каждый раз, когда лицензированный элемент управления добавляется в форму.  Для проекта существует только один LICX\-файл; он всегда хранится в корневой папке и всегда имеет имя Licenses.licx.  
  
 **Чтобы исправить эту ошибку**  
  
-   Переустановите [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## См. также  
 [How to: License Components and Controls](../Topic/How%20to:%20License%20Components%20and%20Controls.md)