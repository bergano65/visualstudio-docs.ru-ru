---
title: "Интерфейс IMachineDebugManagerCookie | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IMachineDebugManagerCookie interface
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a03b959a7eb09f3b85530bbba07d1d2dc7f8948a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagercookie-interface"></a>Интерфейс IMachineDebugManagerCookie
Аналогично `IMachineDebugManager` интерфейс, `IMachineDebugManagerCookie` интерфейс поддерживает файлы cookie отладки.  
  
 Этот интерфейс (вместе с `IDebugCookie` интерфейса) для запуска в процессе отладчика сценариев без необходимости, что отладчик хранить список этих скриптов сценариев.  
  
 Вызывает отладчик сценариев `IDebugCookie::SetDebugCookie` метод на процесс отладки Manager (PDM). Затем PDM отправляет этот файл cookie, а также любой запрос на добавление или удаление приложения сценария в или из Machine Debug Manager (MDM), с помощью методов `IMachineDebugManagerCookie` интерфейса. Затем MDM уведомляет каждый отладчик изменения, за исключением того, который имеет этому файлу cookie.  
  
 Помимо методов, наследуемых от `IUnknown`, `IMachineDebugManagerCookie` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Добавляет приложение с запуском список приложений.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Возвращает перечислитель для текущего списка запущенных приложений.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Удаляет приложение с запуском список приложений.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IMachineDebugManager](../../winscript/reference/imachinedebugmanager-interface.md)   
 [Интерфейс IDebugCookie](../../winscript/reference/idebugcookie-interface.md)