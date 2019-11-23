---
title: Перечисление АППБРЕАКФЛАГС | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- APPBREAKFLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- APPBREAKFLAGS constants
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de6efbc20843fcaa73965334c18cf0e5c2a0abab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572660"
---
# <a name="appbreakflags-enumeration"></a>Перечисление APPBREAKFLAGS
Показывают текущее состояние отладки для приложений и потоков.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_APPBREAKFLAGS{APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,APPBREAKFLAG_STEP= 0x00010000,APPBREAKFLAG_NESTED= 0x00020000,APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,APPBREAKFLAG_IN_BREAKPOINT= 0x80000000};  
```  
  
## <a name="members"></a>Members  
  
|Член|Значение|Описание|  
|------------|-----------|-----------------|  
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|Модуль языка должен немедленно переключиться на все потоки с BREAKREASON_DEBUGGER_BLOCK.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|Модуль языка должен немедленно прерывать работу с BREAKREASON_DEBUGGER_HALT.|  
|APPBREAKFLAG_STEP|0x00010000|Модуль языка должен немедленно прерывать работу в потоке пошагового выполнения с BREAKREASON_STEP.|  
|APPBREAKFLAG_NESTED|0x00020000|Приложение находится во вложенном исполнении в точке останова.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|Отладчик проходит по шагам на исходном уровне.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|Отладчик проходит по шагам на уровне байтового кода.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|Отладчик проходит по шагам на уровне компьютера.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|Маска для разложения типов шагов.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|Точка останова выполняется.|  
  
## <a name="remarks"></a>Примечания  
 Некоторые флаги указывают, что обработчики языка должны прерываться при следующей возможности, а другие флаги указывают режим пошагового отладчика.  
  
## <a name="see-also"></a>См. также:  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [Перечисление BREAKREASON](../../winscript/reference/breakreason-enumeration.md)