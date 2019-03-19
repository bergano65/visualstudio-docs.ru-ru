---
title: Интерфейс ISimpleConnectionPoint | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ISimpleConnectionPoint interface
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d18c8f9eef6ddb1a38473eb19984bd9cf7dbd96
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146933"
---
# <a name="isimpleconnectionpoint-interface"></a>Интерфейс ISimpleConnectionPoint
Предоставляет простой способ для описания и перечисление событий, произошедших в конкретной точке подключения. Этот интерфейс также позволяет легко подключить `IDispatch` объекта на эти события. Этот интерфейс реализуется путем процесс отладки Manager (PDM) и потребляемых обработчиков сценариев.  
  
 Этот интерфейс доступен из `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Помимо методов, наследуемых от `IUnknown`, `ISimpleConnectionPoint` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Устанавливает соединение между объектом точки простого подключения и приемника клиента.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Возвращает идентификатор DISPID и имя для каждого события в указанном диапазоне событий.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Возвращает количество событий, предоставленных на этом интерфейсе.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Завершает вспомогательное соединение, установленное ранее при помощи `ISimpleConnectionPoint::Advise`.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)