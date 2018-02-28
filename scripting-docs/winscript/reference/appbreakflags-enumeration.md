---
title: "Перечисление APPBREAKFLAGS | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- APPBREAKFLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- APPBREAKFLAGS constants
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 126dcd704a60b591b71913f2e8e739de35c14636
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="appbreakflags-enumeration"></a>Перечисление APPBREAKFLAGS
Показывают текущее состояние отладки для приложений и потоков.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_APPBREAKFLAGS{APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,APPBREAKFLAG_STEP= 0x00010000,APPBREAKFLAG_NESTED= 0x00020000,APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,APPBREAKFLAG_IN_BREAKPOINT= 0x80000000};  
```  
  
## <a name="members"></a>Члены  
  
|Член|Значение|Описание|  
|------------|-----------|-----------------|  
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|Языковая подсистема следует прерывать сразу все потоки с BREAKREASON_DEBUGGER_BLOCK.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|Языковая подсистема следует немедленное прерывание с BREAKREASON_DEBUGGER_HALT.|  
|APPBREAKFLAG_STEP|0x00010000|Языковая подсистема следует немедленное прерывание в пошагового выполнения потока с BREAKREASON_STEP.|  
|APPBREAKFLAG_NESTED|0x00020000|Данное приложение находится в вложенное выполнение в точке останова.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|Отладчик является выход на уровне источника.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|Отладчик является выход на уровне кода байтов.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|Отладчик является выход на уровне компьютера.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|Маска для разложения типов шагов.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|Точки останова уже выполняется.|  
  
## <a name="remarks"></a>Примечания  
 Некоторые флаги определяют, что модули языка должно быть прервано в первой возможности, пока другие флаги режим пошагового режима отладчика.  
  
## <a name="see-also"></a>См. также  
 [Константы отладчика активных скриптов, перечисления и структуры](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [Перечисление BREAKREASON](../../winscript/reference/breakreason-enumeration.md)