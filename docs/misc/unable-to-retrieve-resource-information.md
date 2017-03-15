---
title: "Unable to retrieve resource information | Microsoft Docs"
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
  - "vs.tasklisterror.resx_scan_failed"
ms.assetid: e4389ff0-eb64-4c31-b32f-5216c73fadfb
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to retrieve resource information
Поиск RESX\-файлов в иерархической структуре проекта завершился неудачей.  
  
 В процессе построения на этапе `Preparing resources`, отображаемом в окне **Выходные данные**, система работы с проектами просматривает иерархическую структуру проекта, чтобы найти все файлы с расширением RESX.  В результате создается список XML\-файлов типа RESX, которые необходимо преобразовать в двоичные файлы ресурсов перед тем, как они будут включены в качестве ресурсов в выходной файл проекта.  
  
 **Чтобы исправить эту ошибку**  
  
-   Перезапустите [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Если это не поможет, обратитесь в службу технической поддержки Майкрософт.  
  
     При возникновении этой ошибки процесс построения завершается неудачей.  
  
## См. также  
 [File Types and File Extensions in Visual Basic and Visual C\#](http://msdn.microsoft.com/ru-ru/f793852c-da06-4d52-a826-65f635844772)