---
title: Интерфейс IMachineDebugManagerEvents | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: fcfcc2aed0fedefdc149b83e911d33cd3b54cdef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977634"
---
# <a name="imachinedebugmanagerevents-interface"></a>Интерфейс IMachineDebugManagerEvents
Сигнализирует об изменениях в списке запущенных приложений, формируемом диспетчером отладки. Этот интерфейс может использоваться отладчиком интегрированной среды разработки для отображения динамического списка приложений.  
  
 Помимо методов, наследуемых от `IUnknown`, `IMachineDebugManagerEvents` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Обрабатывает событие при добавлении приложения с запуском список приложений.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Обрабатывает событие, когда приложение удаляется из выполняемого список приложений.|