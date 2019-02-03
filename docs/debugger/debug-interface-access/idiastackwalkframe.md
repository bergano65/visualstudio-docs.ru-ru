---
title: IDiaStackWalkFrame | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf14665b4a8f6f57e01d53debedbb3534fa025d1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015490"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
Поддерживает контекст стека между вызовами [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaStackWalkFrame`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Получает значение регистра.|  
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Задает значение регистра.|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Читает содержимое памяти на основе образа.|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Выполняет поиск указанного кадра стека для ближайшего обратный адрес функции.|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Выполняет поиск указанного кадра стека для возврата адреса близка к указанному адресу.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс используется во время выполнения программы для чтения и записи регистров, а также доступ к памяти и найти обратный адрес.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Клиентское приложение реализует этот интерфейс и передает экземпляр интерфейса, который [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md) метод. Один и тот же экземпляр этого интерфейса используется повторно для поддержания состояния регистров при каждом вызове `execute` метод. `execute` Метод также использует этот интерфейс, чтобы определить обратный адрес.  
  
## <a name="requirements"></a>Требования  
 Заголовок: dia2.h  
  
 Библиотека: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также раздел  
 [Интерфейсы (пакет SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)