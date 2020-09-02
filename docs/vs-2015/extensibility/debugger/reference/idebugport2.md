---
title: IDebugPort2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c9227e2e05499feac628a5b90fc6e3d2a4399992
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188566"
---
# <a name="idebugport2"></a>IDebugPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет порт отладки на компьютере.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Пользовательский поставщик портов реализует этот интерфейс для представления порта отладки на компьютере.  
  
 Если порт поддерживает отправку событий порта, он также должен реализовать <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> интерфейс для поддержки <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> интерфейса, который, в свою очередь, предоставляет интерфейс [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) .  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовы метода [Port](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) или [аддпорт](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) возвращают этот интерфейс, представляющий запрошенный порт.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugPort2` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Возвращает имя порта.|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Возвращает идентификатор порта.|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Возвращает запрос, используемый для создания порта (если он доступен).|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Возвращает поставщика порта для этого порта.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Возвращает интерфейс для процесса с учетом идентификатора процесса.|  
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Перечисляет все процессы, запущенные в порте.|  
  
## <a name="remarks"></a>Remarks  
 Локальный порт предоставляет доступ ко всем процессам и программам, выполняемым на локальном компьютере. Другие порты могут представлять подключение последовательного кабеля к устройству на основе Windows CE или сетевое подключение к компьютеру, не являющемуся DCOM. `IDebugPort2`Интерфейс используется для поиска имени и идентификатора порта, перечисления всех процессов, запущенных в порте, и предоставления средств для запуска и завершения процессов в порте.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
