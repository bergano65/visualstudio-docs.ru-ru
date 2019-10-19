---
title: Интерфейс IMachineDebugManagerCookie | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerCookie interface
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b39c286f389c99187b0f3250fc68af92ff5dcc8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573884"
---
# <a name="imachinedebugmanagercookie-interface"></a>Интерфейс IMachineDebugManagerCookie
Подобно интерфейсу `IMachineDebugManager`, интерфейс `IMachineDebugManagerCookie` поддерживает файлы cookie отладки.  
  
 Этот интерфейс (вместе с интерфейсом `IDebugCookie`) позволяет выполнять скрипты в процессе отладчика скриптов, не требуя от отладчика отследить эти скрипты.  
  
 Отладчик скриптов вызывает метод `IDebugCookie::SetDebugCookie` в диспетчере отладки процессов (PDM). Затем PDM отправляет этот файл cookie вместе с любым запросом на добавление или удаление приложения скрипта в диспетчере отладки (MDM) с помощью методов интерфейса `IMachineDebugManagerCookie`. Затем MDM уведомляет каждый отладчик об изменении, за исключением того, что имеет этот файл cookie.  
  
 В дополнение к методам, унаследованным от `IUnknown`, интерфейс `IMachineDebugManagerCookie` предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Добавляет приложение в список выполняющихся приложений.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Возвращает перечислитель текущего списка выполняющихся приложений.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Удаляет приложение из списка выполняющихся приложений.|  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса имачинедебугманажер](../../winscript/reference/imachinedebugmanager-interface.md)  
 [Интерфейс IDebugCookie](../../winscript/reference/idebugcookie-interface.md)