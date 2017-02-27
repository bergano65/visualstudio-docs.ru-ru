---
title: "IDiaStackWalkHelper | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackWalkHelper2 - интерфейс"
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IDiaStackWalkHelper
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Facilitates гуляя стек с помощью программы отладки файла базы данных \(.pdb\).  
  
## Синтаксис  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## Методы в том порядке VTable  
 В таблице ниже приведены методы `IDiaStackWalkHelper`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDiaStackWalkHelper::get\_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|Извлекает значение регистра.|  
|[IDiaStackWalkHelper::put\_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Устанавливает значение регистра.|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Считывает блок данных из образа исполняемого файла в памяти.|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Ищет указанный кадр стека для ближайшего обратного адреса функции.|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../Topic/IDiaStackWalkHelper::searchForReturnAddressStart.md)|Ищет указанный кадр стека для обратного адреса или собирается указанный адрес стека.|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Извлекает кадр стека, который содержит указанный виртуальный адрес.|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Получает символ, который содержит указанный виртуальный адрес. **Note:**  Символ должен иметь тип `SymTagFunctionType` \(значение  [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) перечисление\).|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Возвращает фрагмент данных PDATA, связанный с указанным виртуальным адресом.|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Получает начальный виртуальный адрес исполняемого заданный виртуальный адрес расположения в области памяти исполняемого файла.|  
  
## Заметки  
 Этот интерфейс, вызывается кодом DIA для получения сведений о исполняемом файле для построения списка кадров стека во время выполнения программы.  
  
## Замечания для вызывающих объектов  
 Клиентское приложение реализует этот интерфейс для поддержки прохода по стеку во время выполнения программы.  Экземпляр данного интерфейса передается [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) OR  [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) методы.  
  
## Требования  
 Заголовок: Dia2.h  
  
 Библиотеки: diaguids.lib  
  
 Библиотеки DLL: msdia80.dll  
  
## См. также  
 [Интерфейсы \(SDK для доступа к интерфейсу отладки\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)