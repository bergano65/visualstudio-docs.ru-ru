---
title: "IDiaStackWalkFrame | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be50964aaadad30aa13d6627be2ad1637e6123b3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
Поддерживает стек контекста между вызовами [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaStackWalkFrame`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Извлекает значение регистра.|  
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Задает значение регистра.|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Считывает память из образа.|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Выполняет указанный кадр стека для ближайшего обратный адрес функции.|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Выполняет указанный кадр стека для обратный адрес близка к указанному адресу.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс используется во время выполнения программы для чтения и записи регистров, а также доступ к памяти и найти обратный адрес.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Клиентское приложение реализует этот интерфейс и передает экземпляр интерфейса, который [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md) метод. Снова и снова используется один и тот же экземпляр этого интерфейса для поддержания состояния регистров при каждом вызове `execute` метода. `execute` Метод также использует этот интерфейс, чтобы определить адрес возврата.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотека DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)