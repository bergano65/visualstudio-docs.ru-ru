---
title: IDebugCoreServer2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 14
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 31961d62c2ef7a253a16a5384dfa6b5e69209a97
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Этот интерфейс используется для представления и получения сведений с сервера на компьютере в сети.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Visual Studio реализует этот интерфейс для представления на сервере. Каждый экземпляр Visual Studio создает экземпляр этого интерфейса.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Пользовательский порт поставщика получает этот интерфейс в вызове [событие](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Модуль отладки можно получить этот интерфейс косвенно посредством вызова [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (возвращающий [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), интерфейс, который является производным от `IDebugCoreServer2`).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugCoreServer2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Возвращает имя и атрибуты машины.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Получает имя компьютера.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Возвращает поставщика порта, который существует на компьютере.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Возвращает порт, который уже существует на компьютере.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Создает перечислитель для всех портов на компьютере.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Создает перечислитель для всех поставщиков, порт на компьютере.|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Возвращает программы машины для машины.|  
  
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