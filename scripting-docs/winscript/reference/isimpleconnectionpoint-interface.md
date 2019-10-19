---
title: Интерфейс Исимплеконнектионпоинт | Документация Майкрософт
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
ms.openlocfilehash: 549d7f38b01937f992b240cb6f1d651bc848236c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571789"
---
# <a name="isimpleconnectionpoint-interface"></a>Интерфейс ISimpleConnectionPoint
Предоставляет простой способ описания и перечисления событий, инициированных в определенной точке соединения. Этот интерфейс также упрощает подключение объекта `IDispatch` к этим событиям. Этот интерфейс реализуется диспетчером отладки процессов (PDM) и используется обработчиками скриптов.  
  
 Этот интерфейс доступен из `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 В дополнение к методам, унаследованным от `IUnknown`, интерфейс `ISimpleConnectionPoint` предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Устанавливает соединение между простым объектом точки подключения и приемником клиента.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Возвращает идентификатор DISPID и имя для каждого события в указанном диапазоне событий.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Возвращает число событий, предоставленных для этого интерфейса.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Завершает подключение рекомендаций, установленное ранее с помощью `ISimpleConnectionPoint::Advise`.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)