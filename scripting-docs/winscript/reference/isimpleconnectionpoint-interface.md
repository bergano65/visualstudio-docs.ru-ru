---
title: "Интерфейс ISimpleConnectionPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "ISimpleConnectionPoint — интерфейс"
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс ISimpleConnectionPoint
Предоставляет простой способ для описания события сгоренный и перечисления в указанной точке подключения.  Этот интерфейс также делает его простым подключить объект `IDispatch` к этим событиям.  Этот интерфейс реализуется отростчатым диспетчером отладки \(PDM\) и использоваться командами сценария.  
  
 Этот интерфейс доступен из `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `ISimpleConnectionPoint` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Устанавливает связь между простой объект точки подключения и приемник клиента.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Возвращает идентификатор DISPID и имя каждого события в указанном диапазоне событий.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Возвращает количество событий, предоставляемых в этом интерфейсе.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Завершает вспомогательное подключение, установленное ранее при помощи `ISimpleConnectionPoint::Advise`.|  
  
## См. также  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)