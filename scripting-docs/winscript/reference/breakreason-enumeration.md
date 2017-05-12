---
title: "Перечисление BREAKREASON | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKREASON
apilocation: scrobj.dll
helpviewer_keywords: 
  - "BREAKREASON — перечисление"
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Перечисление BREAKREASON
Указывает, что вызвавшее прерывание.  
  
## Синтаксис  
  
```  
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## Члены  
  
|Элемент|Описание|  
|-------------|--------------|  
|BREAKREASON\_STEP|Обработчик языка в режиме пошагового выполнения.|  
|BREAKREASON\_BREAKPOINT|Обработчик языка обнаружил явная точка останова.|  
|BREAKREASON\_DEBUGGER\_BLOCK|Обработчик языка обнаружил блок отладчика в другом потоке.|  
|BREAKREASON\_HOST\_INITIATED|Основное приложение запросила break.|  
|BREAKREASON\_LANGUAGE\_INITIATED|Обработчик языка запросил прерывание.|  
|BREAKREASON\_DEBUGGER\_HALT|Интегрированная среда разработки запрашивается прерывания отладчика.|  
|BREAKREASON\_ERROR|Ошибка выполнения, вызвавшая прерывание.|  
|BREAKREASON\_JIT|Причиненный запуском JIT\-отладка.|  
  
## См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)