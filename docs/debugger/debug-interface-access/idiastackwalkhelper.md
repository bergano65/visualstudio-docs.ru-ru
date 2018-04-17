---
title: IDiaStackWalkHelper | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 881fcbb4f019ad9cb6321423c12269fb6e3ad78f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
Облегчает прохода по стеку, с помощью программы отладки PDB-файла.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы VTable  
 В следующей таблице показаны методы `IDiaStackWalkHelper`:  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|Извлекает значение регистра.|  
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Задает значение регистра.|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Считывает блок данных из исполняемого файла изображения в памяти.|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Выполняет указанный кадр стека для ближайшего обратный адрес функции.|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Выполняет указанный кадр стека для обратный адрес близка к указанным стековый адрес.|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Извлекает кадру стека, который содержит указанный виртуальный адрес.|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Возвращает символ, который содержит указанный виртуальный адрес. **Примечание:** символ должен иметь тип `SymTagFunctionType` (значение из [SymTagEnum-перечисление](../../debugger/debug-interface-access/symtagenum.md) перечисления).|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Возвращает PDATA блок данных, сопоставленный указанному виртуальному адресу.|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Извлекает Начальный виртуальный адрес исполняемого файла, указанного виртуального адреса где-либо в области памяти исполняемого файла.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс называется кодом доступа к интерфейсу отладки для получения сведений о исполняемый файл, чтобы создать список из кадров стека во время выполнения программы.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Клиентское приложение реализует этот интерфейс для поддержки прохода по стеку во время выполнения программы. Экземпляр этого интерфейса передается [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) или [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) методы.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотека DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)