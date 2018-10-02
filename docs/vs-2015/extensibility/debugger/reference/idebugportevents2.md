---
title: IDebugPortEvents2 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3eb6208d815e4951bd916d014cddfdda34a8e589
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563339"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugPortEvents2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportevents2).  
  
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
  
|Метод|Описание|  
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

