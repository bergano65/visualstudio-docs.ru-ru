---
title: Перечисление APPBREAKFLAGS | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 49d9cef3583def8cd23e135b960e46979446b3bb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349027"
---
# <a name="appbreakflags-enumeration"></a>Перечисление APPBREAKFLAGS
Показывают текущее состояние отладки для приложений и потоков.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_APPBREAKFLAGS{APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,APPBREAKFLAG_STEP= 0x00010000,APPBREAKFLAG_NESTED= 0x00020000,APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,APPBREAKFLAG_IN_BREAKPOINT= 0x80000000};  
```  
  
## <a name="members"></a>Участники  
  
|Член|Значение|Описание:|  
|------------|-----------|-----------------|  
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|Модуль языка должно прерывать работу немедленно во всех потоках с BREAKREASON_DEBUGGER_BLOCK.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|Модуль языка должно прерывать работу немедленно с BREAKREASON_DEBUGGER_HALT.|  
|APPBREAKFLAG_STEP|0x00010000|Модуль языка должно прерывать работу немедленно в потоке пошагового выполнения с BREAKREASON_STEP.|  
|APPBREAKFLAG_NESTED|0x00020000|Приложение находится в вложенное выполнение в точке останова.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|Отладчик является выход на уровне источника.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|Отладчик является выход на уровне кода байтов.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|Отладчик является выход на уровне компьютера.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|Маска для разложения типов шагов.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|Точки останова уже выполняется.|  
  
## <a name="remarks"></a>Примечания  
 Некоторые флаги указать, что модулям языка будет прерываться в осуществляется при первой возможности, хотя другие флаги режим пошагового выполнения отладчика.  
  
## <a name="see-also"></a>См. также  
 [Константы отладчика активных скриптов, перечисления и структуры](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [Перечисление BREAKREASON](../../winscript/reference/breakreason-enumeration.md)