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
ms.openlocfilehash: fdc02498360f2e3900012166474c5d1e35abd6ee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977689"
---
# <a name="imachinedebugmanagercookie-interface"></a>Интерфейс IMachineDebugManagerCookie
Аналогичную `IMachineDebugManager` интерфейс, `IMachineDebugManagerCookie` интерфейс поддерживает файлы cookie отладки.  
  
 Этот интерфейс (вместе с `IDebugCookie` интерфейса) для запуска в процессе отладчика сценариев без необходимости, что отладчик хранить список этих скриптов сценариев.  
  
 Вызывает отладчик сценариев `IDebugCookie::SetDebugCookie` метод на процесс отладки Manager (PDM). Затем PDM отправляет этот файл cookie, а также любой запрос, чтобы добавить или удалить приложение сценария для или от машины отладка Manager (MDM), с помощью методов `IMachineDebugManagerCookie` интерфейс. MDM уведомляет каждый отладчик изменения, за исключением того, который содержит этот файл cookie.  
  
 Помимо методов, наследуемых от `IUnknown`, `IMachineDebugManagerCookie` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Добавляет приложению выполнения список приложений.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Возвращает перечислитель текущего списка выполняющихся приложений.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Удаляет приложение из выполняемого список приложений.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IMachineDebugManager](../../winscript/reference/imachinedebugmanager-interface.md)   
 [Интерфейс IDebugCookie](../../winscript/reference/idebugcookie-interface.md)