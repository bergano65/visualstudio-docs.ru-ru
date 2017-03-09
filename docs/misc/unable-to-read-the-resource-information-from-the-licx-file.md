---
title: "Unable to read the resource information from the licx file | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.fail_reading_licx_file"
ms.assetid: e59f0965-fa1c-4852-bd39-63430d5b7d9f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to read the resource information from the licx file
Система работы с проектами не может прочитать LICX\-файл.  В процессе подготовки лицензий система работы с проектами преобразует текстовые LICX\-файлы в двоичные файлы ресурсов, пригодные для использования в модели лицензирования COM\+.  
  
 LICX\-файл автоматически создается или обновляется конструктором Windows Forms каждый раз, когда лицензированный элемент управления добавляется в форму.  Для проекта существует только один LICX\-файл; он всегда хранится в корневой папке и всегда имеет имя Licenses.licx.  
  
 Ниже перечислены возможные причины ошибки.  
  
-   Доступ запрещен.  
  
-   Потеряна связь с веб\-сервером для веб\-проектов.  
  
 При возникновении этой ошибки процесс построения завершается неудачей.  
  
## См. также  
 [How to: License Components and Controls](../Topic/How%20to:%20License%20Components%20and%20Controls.md)