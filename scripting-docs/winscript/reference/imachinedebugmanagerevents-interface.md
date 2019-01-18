---
title: Интерфейс IMachineDebugManagerEvents | Документация Майкрософт
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
ms.openlocfilehash: f9aab3d7abeecd22e830c68f174896df0e7df2da
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344042"
---
# <a name="imachinedebugmanagerevents-interface"></a>Интерфейс IMachineDebugManagerEvents
Сигнализирует об изменениях в списке запущенных приложений, формируемом диспетчером отладки. Этот интерфейс может использоваться отладчиком интегрированной среды разработки для отображения динамического списка приложений.  
  
 Помимо методов, наследуемых от `IUnknown`, `IMachineDebugManagerEvents` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Обрабатывает событие при добавлении приложения с запуском список приложений.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Обрабатывает событие, когда приложение удаляется из выполняемого список приложений.|