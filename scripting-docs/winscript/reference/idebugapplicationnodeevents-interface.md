---
title: Интерфейс IDebugApplicationNodeEvents | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNodeEvents interface
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7412e258c7f67f44bde6f69b593a1eecb1d84e07
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150519"
---
# <a name="idebugapplicationnodeevents-interface"></a>Интерфейс IDebugApplicationNodeEvents
Предоставляет интерфейс событий для интерфейса `IDebugApplicationNode`.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugApplicationNodeEvents` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Обрабатывает событие, когда дочерний узел добавляется в объект узла отладки приложения.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Обрабатывает событие, когда дочерний узел удаляется из объект узла отладки приложения.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Обрабатывает событие, которое означает, что объект узла отладки приложения была отсоединена от родительского узла.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Обрабатывает событие, которое означает, что объект узла отладки приложения был присоединен к родительскому узлу.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)