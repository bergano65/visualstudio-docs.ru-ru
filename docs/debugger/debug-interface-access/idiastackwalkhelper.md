---
title: IDiaStackWalkHelper | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0143945a266b9c76fefa10e1823a7c3ce01f85e7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837840"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
Упрощает анализ стека с помощью PDB-файла программы отладки.

## <a name="syntax"></a>Синтаксис

```

IDiaStackWalkHelper: IUnknown

```

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDiaStackWalkHelper`:

|Метод|Описание|
|------------|-----------------|
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|Получает значение регистра.|
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Задает значение регистра.|
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Считывает блок данных из исполняемого файла изображения в памяти.|
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Выполняет поиск указанного кадра стека для ближайшего обратный адрес функции.|
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Выполняет поиск указанного кадра стека для возврата адреса сравнялось или почти адрес указанного стека.|
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Извлекает кадру стека, который содержит указанный виртуальный адрес.|
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Получает символ, который содержит указанный виртуальный адрес. **Примечание.**  Символ должен иметь тип `SymTagFunctionType` (значение из [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) перечисления).|
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Возвращает блок данных PDATA, связанный с указанным адресом виртуальной.|
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Извлекает Начальный виртуальный адрес исполняемого файла, указанного виртуального адреса где-то в область памяти.|

## <a name="remarks"></a>Примечания
 Этот интерфейс называется кодом доступа к интерфейсу отладки, для получения сведений о исполняемый файл для создания списка из кадров стека во время выполнения программы.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Клиентское приложение реализует этот интерфейс для поддержки прохода по стеку во время выполнения программы. Экземпляр этого интерфейса передается [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) или [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) методы.

## <a name="requirements"></a>Требования
 Заголовок: dia2.h

 Библиотека: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>См. также
- [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)