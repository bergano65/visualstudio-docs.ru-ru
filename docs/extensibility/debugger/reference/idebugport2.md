---
title: "IDebugPort2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPort2
helpviewer_keywords: IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 91ee83167c681b713ea7d7a51a38d45b05fba4d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugport2"></a>IDebugPort2
Этот интерфейс представляет порт отладки на компьютере.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Поставщик пользовательский порт реализует этот интерфейс для представления порта отладки на компьютере.  
  
 Если порт поддерживает отправлять события портов, необходимо также реализовать <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> интерфейс для поддержки <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> интерфейс, который в свою очередь предоставляет [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) интерфейса.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовы [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) или [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) возвращают этот интерфейс, представляющий запрошенный порт.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugPort2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Возвращает имя порта.|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Возвращает идентификатор порта.|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Возвращает запрос, используемый для создания порта (если доступно).|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Возвращает поставщика порта для этого порта.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Возвращает интерфейс процесс, Получает идентификатор процесса.|  
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Перечисляет все процессы, запущенные на порт.|  
  
## <a name="remarks"></a>Примечания  
 Локальный порт предоставляет доступ ко всем процессам и программы, запущенные на локальном компьютере. Другим портам, может представлять подключения к последовательному на устройстве под управлением Windows CE или сетевое подключение к компьютеру не DCOM. `IDebugPort2` Интерфейс используется для поиска, имя и идентификатор порта, перечислить все процессы, запущенные на порт и предоставляет средства для запуска и завершения процессов в порт.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)