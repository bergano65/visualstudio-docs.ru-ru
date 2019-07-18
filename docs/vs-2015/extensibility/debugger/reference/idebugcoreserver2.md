---
title: IDebugCoreServer2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c0bca6ccd3738518df339084b0f6463be181e52d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192917"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс используется для представления и получения сведений с сервера на компьютере в сети.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Visual Studio реализует этот интерфейс для представления сервера. Каждый экземпляр Visual Studio создает экземпляр этого интерфейса.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Пользовательский порт поставщика получает этот интерфейс в вызове [событий](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Модуль отладки можно получить этот интерфейс косвенно посредством вызова [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (который возвращает [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), интерфейс, который является производным от `IDebugCoreServer2`).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugCoreServer2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Получает имя и атрибуты машины.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Возвращает имя машины.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Получает поставщика порта, который существует на компьютере.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Получает порт, который уже существует на компьютере.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Создает перечислитель для всех портов на компьютере.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Создает перечислитель для всех поставщиков, порт на компьютере.|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Получает служебные программы машины для машины.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс также используется в Visual Studio для просмотра процессов, запущенных на компьютерах в сети.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
