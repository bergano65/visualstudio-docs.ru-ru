---
title: "Ограничения длины строки | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "управление подключаемыми модулями источников, ограничения длины строки"
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Ограничения длины строки
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

API подключаемого модуля управления источника ограничивает длину строк, используемых в различных функций.  
  
## Значения длины строк  
  
|Константа|Значение|  
|---------------|--------------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  Длина не включает конечный символ `null`. Другие константы с суффиксом «ра\_змер» вместо «\_LEN» включает свободное место для завершения `null`.  
  
|Константа|Значение|  
|---------------|--------------|  
|SCC\_NAME\_SIZE|32|  
|SCC\_AUXLABEL\_SIZE|32|  
|SCC\_USER\_SIZE|32|  
|SCC\_PRJPATH\_SIZE|301|  
  
## См. также  
 [Подключаемые модули управления версиями](../extensibility/source-control-plug-ins.md)