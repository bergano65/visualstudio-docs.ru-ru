---
title: "Перечисление SCRIPTLANGUAGEVERSION | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Перечисление SCRIPTLANGUAGEVERSION
Задает возможные сценарии версии.  
  
## Синтаксис  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION  
{  
    SCRIPTLANGUAGEVERSION_DEFAULT = 0,  
    SCRIPTLANGUAGEVERSION_5_7  = 1,  
    SCRIPTLANGUAGEVERSION_5_8  = 2,  
    SCRIPTLANGUAGEVERSION_MAX  = 255  
} SCRIPTLANGUAGEVERSION ;  
  
```  
  
## Значения перечисления  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION\_DEFAULT|Версия по умолчанию.  Целое число 0.|  
|SCRIPTLANGUAGEVERSION\_5\_7|Создание сценариев Windows версии 5.7.  Целое число 1.|  
|SCRIPTLANGUAGEVERSION\_5\_8|Создание сценариев Windows версии 5.8.  Целое число 2.|  
|SCRIPTLANGUAGEVERSION\_MAX|Максимальная версия.  Целое число 255.|  
  
## См. также  
 [Константы, перечисления и коды ошибок активных скриптов](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)