---
title: Интерфейс IScriptEntry | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptEntry interface
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 868322358908a32c8f14b56846cf3237f8531b4c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575395"
---
# <a name="iscriptentry-interface"></a>Интерфейс IScriptEntry
Объект, реализующий интерфейс `IScriptEntry`, представляет либо блок скрипта, либо объект функции.  
  
 В дополнение к методам, унаследованным от `IScriptNode`, интерфейс `IScriptEntry` предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Возвращает текст, соответствующий телу блока `IScriptEntry` скрипта, блока Function или скриптлет.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Возвращает имя элемента, идентифицирующего объект `IScriptEntry`.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Для записей, представляющих один объект (например, функцию), возвращает имя объекта.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Возвращает начальную и длину записи.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Возвращает сведения о типе для объекта `IScriptEntry` функции.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Возвращает текст, соответствующий блоку сценария `IScriptEntry` или исходному коду, содержащемуся в обработчике событий `IScriptScriptlet`.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Задает текст, который находится в теле блока `IScriptEntry` скрипта или `IScriptScriptlet` скриптлет.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Задает имя элемента, идентифицирующего объект `IScriptEntry`.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Для записей, представляющих один объект (например, функцию), задает имя объекта.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Задает сведения о типе для объекта `IScriptEntry` функции.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Задает текст, соответствующий блоку `IScriptEntry` сценария, или исходный код, содержащийся в обработчике событий `IScriptScriptlet`.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы для создания активных скриптов](../../winscript/reference/active-script-authoring-interfaces.md)