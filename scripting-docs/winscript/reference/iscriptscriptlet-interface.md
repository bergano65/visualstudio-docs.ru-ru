---
title: Интерфейс IScriptScriptlet | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptScriptlet interface
ms.assetid: b9981908-a337-4228-864c-c741f111ab2d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c11aada6b8c39c7dd5f0b2a6b30cdd837aa0edda
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786715"
---
# <a name="iscriptscriptlet-interface"></a>Интерфейс IScriptScriptlet
Объект, реализующий `IScriptScriptlet` интерфейс представляет сценарий обработчика событий.  
  
 Помимо методов, наследуемых от `IScriptEntry`, `IScriptScriptlet` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|Возвращает имя события, который связан со скриптлетом.|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|Возвращает имя простых событий, который связан с пользователи. Это имя одного слова, которое не содержит пробелов.|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|Возвращает последний идентификатор в полное имя узла объекта скриптлета.|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|Задает имя события, связанные со скриптлетом.|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|Задает имя простого события, который связан с пользователи. Это имя одного слова, которое не содержит пробелов.|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|Задает идентификатор последнего в полное имя узла объекта скриптлета.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы для создания активных скриптов](../../winscript/reference/active-script-authoring-interfaces.md)