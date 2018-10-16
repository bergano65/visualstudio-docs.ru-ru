---
title: Интерфейс IMachineDebugManagerEvents | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerEvents interface
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 369dc8d182efe7bf9697454d0e4b1c9c1a10c027
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727634"
---
# <a name="imachinedebugmanagerevents-interface"></a>Интерфейс IMachineDebugManagerEvents
Указывает изменения в работе приложения списка, поддерживаемого диспетчера отладки. Этот интерфейс можно использовать отладчик интегрированной среды разработки для отображения динамического списка приложений.  
  
 Помимо методов, наследуемых от `IUnknown`, `IMachineDebugManagerEvents` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Обрабатывает событие, при добавлении приложения с запуском список приложений.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Обрабатывает событие, когда приложение удаляется из выполнения список приложений.|