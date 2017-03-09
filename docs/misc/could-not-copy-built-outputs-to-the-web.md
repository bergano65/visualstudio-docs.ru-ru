---
title: "Не удалось скопировать созданные файлы в Интернет. | Microsoft Docs"
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
  - "vs.tasklisterror.cantcopyoutputstoweb"
ms.assetid: 59cf714b-cf7d-4df9-81ae-d3254969d5bc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Не удалось скопировать созданные файлы в Интернет.
Системе проектов не удалось скопировать один или несколько выходных файлов сборки \(например, собранную библиотеку DLL, PDB\-файл или вспомогательные сборки\) на веб\-сервер.  
  
 Эта ошибка означает, что один или несколько выходных файлов сборки не были скопированы на веб\-сервер.  
  
 Эта ошибка обычно возникает, если выходной файл сборки заблокирован на сервере или доступен там только для чтения. Если файл заблокирован на сервере, значит, среда выполнения [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] неправильно скопировала сборки, вспомогательные сборки или отладочные символы, которые сейчас находятся на сервере.  
  
 Возможно, у сервера недостаточно места на диске или проблемы в сети не позволяют [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] отправить файлы по Интернету.  
  
### Исправление ошибки  
  
1.  Проверьте наличие места на диске.  
  
2.  Если файл заблокирован, перезапустите веб\-сервер, чтобы снять блокировку [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] для затронутых файлов.  
  
## См. также  
 [PDB Files](http://msdn.microsoft.com/ru-ru/1761c84e-8c2c-4632-9649-b5f99964ed3f)