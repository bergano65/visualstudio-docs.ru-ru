---
title: "Интерфейс IDebugApplicationNodeEvents | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNodeEvents — интерфейс"
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IDebugApplicationNodeEvents
Предоставляет интерфейс событий для интерфейса `IDebugApplicationNode`.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IDebugApplicationNodeEvents` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Обрабатывает событие, когда дочерний узел добавить к объекту узла приложения отладки.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Обрабатывает событие, когда дочерний узел удаляется из объекта узла приложения отладки.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Обрабатывает событие знаменующ, что объект узла отладки приложения был наконец удалить из родительского узла.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Обрабатывает событие знаменующ, что был вложен объект узла приложения отладки к родительскому узлу.|  
  
## См. также  
 [Интерфейс IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)