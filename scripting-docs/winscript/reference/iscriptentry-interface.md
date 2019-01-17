---
title: Интерфейс IScriptEntry | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 9d7b33e2e5c90d5c489fe283575b4a2e45671f9a
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349352"
---
# <a name="iscriptentry-interface"></a>Интерфейс IScriptEntry
Объект, реализующий `IScriptEntry` интерфейс представляет блок сценария или объекта функции.  
  
 Помимо методов, наследуемых от `IScriptNode`, `IScriptEntry` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Возвращает текст, соответствующий текст `IScriptEntry` блок скрипта, блока функции или сценария.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Возвращает имя элемента, который идентифицирует `IScriptEntry` объекта.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Для записи, представляющие один объект (например, функцию) возвращает имя объекта.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Возвращает начальное положение и длину запись.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Возвращает сведения о типе для `IScriptEntry` объект функции.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Возвращает текст, который соответствует `IScriptEntry` блок сценария, или исходный код, содержащийся в `IScriptScriptlet` обработчик событий.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Задает текст, который находится в теле `IScriptEntry` блок скрипта или `IScriptScriptlet` скриптлета.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Задает имя элемента, который идентифицирует `IScriptEntry` объекта.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Для записи, представляющие один объект (например, функцию) задает имя объекта.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Задает сведения о типе для `IScriptEntry` объект функции.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Задает текст, который соответствует `IScriptEntry` блок сценария, или исходный код, содержащийся в `IScriptScriptlet` обработчик событий.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы для создания активных скриптов](../../winscript/reference/active-script-authoring-interfaces.md)