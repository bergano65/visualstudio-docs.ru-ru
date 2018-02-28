---
title: "Интерфейс IScriptEntry | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IScriptEntry interface
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a785be8777cf3400f7723c24f1022bad6e22e330
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentry-interface"></a>Интерфейс IScriptEntry
Объект, реализующий интерфейс `IScriptEntry` интерфейс представляет собой блок сценария или объекта функции.  
  
 Помимо методов, наследуемых от `IScriptNode`, `IScriptEntry` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Возвращает текст, соответствующий текст `IScriptEntry` блок сценария, функции или сценариев.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Возвращает имя элемента, которое идентифицирует `IScriptEntry` объекта.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Для записей, которые представляют собой один объект (например, функции) возвращает имя объекта.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Возвращает начальную позицию и длину запись.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Возвращает сведения о типе для `IScriptEntry` объект функции.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Возвращает текст, который соответствует `IScriptEntry` блок сценария или исходный код, который содержится в `IScriptScriptlet` обработчика событий.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Задает текст, который находится в теле `IScriptEntry` блок сценария или `IScriptScriptlet` сценариев.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Задает имя элемента, который идентифицирует `IScriptEntry` объекта.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Для операций, которые представляют собой один объект (например, функции) задает имя объекта.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Задает сведения о типе для `IScriptEntry` объект функции.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Задает текст, который соответствует `IScriptEntry` блок сценария или исходный код, который содержится в `IScriptScriptlet` обработчика событий.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы для создания активных скриптов](../../winscript/reference/active-script-authoring-interfaces.md)