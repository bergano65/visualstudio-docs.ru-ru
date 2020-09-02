---
title: Идиастакквалкфраме | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27aab0ca87e589661798028ff38fb019dae815ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150137"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Поддерживает контекст стека между вызовами метода [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaStackWalkFrame` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Возвращает значение регистра.|  
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Задает значение регистра.|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Считывает память из образа.|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Выполняет поиск по указанному кадру стека для ближайшего адреса возврата функции.|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Выполняет поиск адреса возврата в указанном кадре стека по указанному адресу или рядом с ним.|  
  
## <a name="remarks"></a>Remarks  
 Этот интерфейс используется во время выполнения программы для чтения и записи регистров, а также для доступа к памяти и поиска возвращаемых адресов.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Клиентское приложение реализует этот интерфейс и передает экземпляр интерфейса методу [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) . Один и тот же экземпляр этого интерфейса снова используется и снова для поддержания состояния регистров при каждом вызове `execute` метода. `execute`Метод также использует этот интерфейс для определения возвращаемого адреса.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2. h  
  
 Библиотека: диагуидс. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)
