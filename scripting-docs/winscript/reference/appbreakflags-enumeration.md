---
title: "Перечисление APPBREAKFLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: APPBREAKFLAGS
apilocation: scrobj.dll
helpviewer_keywords: 
  - "APPBREAKFLAGS — константы"
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Перечисление APPBREAKFLAGS
Показать, что текущее состояние отладки для приложений и потоков.  
  
## Синтаксис  
  
```cpp  
enum enum_APPBREAKFLAGS  
{  
APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,  
APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,  
APPBREAKFLAG_STEP= 0x00010000,  
APPBREAKFLAG_NESTED= 0x00020000,  
APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,  
APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,  
APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,  
APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,  
APPBREAKFLAG_IN_BREAKPOINT= 0x80000000  
};  
  
```  
  
## Члены  
  
|Элемент|Значение|Описание|  
|-------------|--------------|--------------|  
|APPBREAKFLAG\_DEBUGGER\_BLOCK|0x00000001|Обработчик языка должен прервать непосредственно во всех потоках с BREAKREASON\_DEBUGGER\_BLOCK.|  
|APPBREAKFLAG\_DEBUGGER\_HALT|0x00000002|Обработчик языка должен прервать непосредственно с BREAKREASON\_DEBUGGER\_HALT.|  
|APPBREAKFLAG\_STEP|0x00010000|Обработчик языка должен прервать непосредственно в потоке пошаговое выполнение с BREAKREASON\_STEP.|  
|APPBREAKFLAG\_NESTED|0x00020000|Приложение во вложенных выполнение в точке останова.|  
|APPBREAKFLAG\_STEPTYPE\_SOURCE|0x00000000|Отладчик шагает на уровне источника.|  
|APPBREAKFLAG\_STEPTYPE\_BYTECODE|0x00100000|Отладчик шагает на уровне кода байта.|  
|APPBREAKFLAG\_STEPTYPE\_MACHINE|0x00200000|Отладчик шагает на уровне компьютера.|  
|APPBREAKFLAG\_STEPTYPE\_MASK|0x00F00000|Замаскируйте для вынесения за скобки типы шага.|  
|APPBREAKFLAG\_IN\_BREAKPOINT|0x80000000|Точка останова выполняется.|  
  
## Заметки  
 Некоторые флаги указывают, что обработчики языка должны переключиться на следующей возможности, в то время как другие флаги указывают режим пошагового выполнения отладчика.  
  
## См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [Перечисление BREAKREASON](../../winscript/reference/breakreason-enumeration.md)