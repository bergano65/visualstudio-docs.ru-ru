---
title: "Ошибка: отладка в смешанном режиме для процессов x64 поддерживается только при использовании платформы Microsoft .NET Framework 4 или выше | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.interop_unsupported_x64"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ошибка: отладка в смешанном режиме для процессов x64 поддерживается только при использовании платформы Microsoft .NET Framework 4 или выше
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Для отладки смеси управляемого и неуправляемого кода в 64\-разрядном процессе необходимо использовать версию 4 платформы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Отладка в смешанном режиме для 64\-разрядных процессов при использовании версий [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], предшествующих версии 4, не поддерживается.  
  
### Исправления данной ошибки  
  
-   Выполните одно из следующих действий.  
  
    -   Обновите [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] до версии 4.  
  
    -   Постройте для отладки 32\-разрядную версию приложения.  
  
## См. также  
 [Настройка Инструментов удаленной отладки в устройстве](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)