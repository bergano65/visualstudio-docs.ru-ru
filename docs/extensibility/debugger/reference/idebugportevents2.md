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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 860b03b26c9da4975d4482412214dcc69199de47
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54985150"
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
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)