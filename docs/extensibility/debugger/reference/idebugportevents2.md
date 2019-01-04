---
title: IDebugPortEvents2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d9701fe592e7e357b5f1a89d5bef884d4dbf1ce4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931133"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Этот интерфейс, уведомляет о прослушиватель (обычно диспетчер отладки сеансов [SDM] или модуля отладки), чтобы процесс и программы создания и удаления через определенный порт. Эти сведения можно использовать для представления в режиме реального времени, процессов и программ, работающих на порт.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Visual Studio обычно реализует этот интерфейс для получения уведомлений о программе создания и удаления. Модуль отладки также можно реализовать этот интерфейс для прослушивания событий такой порт.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Все [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) интерфейсы могут запрашиваться <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> интерфейс. Затем <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> метод `IDebugPortEvents2` вызывается в <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> интерфейса для получения <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> интерфейс. Наконец <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> метод в <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> интерфейс вызывается для отправки событий через [событий](../../../extensibility/debugger/reference/idebugportevents2-event.md) метод.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны метод `IDebugPortEvents2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Отправляет события, которые описывают создание и уничтожение процессов и программ на порт.|  
  
## <a name="remarks"></a>Примечания  
 `IDebugPortEvents2` также используется SDM для отладки программ, выполняемых в процессе, который уже отлаживается.  
  
 Порт события передаются SDM этим интерфейсом.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)