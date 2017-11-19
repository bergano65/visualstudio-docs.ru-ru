---
title: "Интерфейс ISimpleConnectionPoint | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: ISimpleConnectionPoint interface
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de40f66a9e5721b8dacac634c6fb77982017c155
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpoint-interface"></a>Интерфейс ISimpleConnectionPoint
Предоставляет простой способ для описания и перечисление событий, произошедших в точке конкретного соединения. Этот интерфейс также позволяет легко подключать `IDispatch` объекта на эти события. Этот интерфейс реализован, процесс отладки Manager (PDM) и используемые обработчиков сценариев.  
  
 Этот интерфейс доступен из `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Помимо методов, наследуемых от `IUnknown`, `ISimpleConnectionPoint` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Устанавливает соединение между объектом точки простого подключения и приемником клиента.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Возвращает идентификатор DISPID и имя для каждого события в указанном диапазоне событий.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Возвращает количество событий, предоставленных на этом интерфейсе.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Завершает вспомогательное соединение, установленное ранее при помощи `ISimpleConnectionPoint::Advise`.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)