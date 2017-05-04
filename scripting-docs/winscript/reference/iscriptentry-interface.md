---
title: "Интерфейс IScriptEntry | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IScriptEntry — интерфейс"
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Интерфейс IScriptEntry
Объект, средства интерфейс `IScriptEntry` представляющие либо блок скрипта или функции.  
  
 В дополнение к методам, наследуемым от интерфейса `IScriptNode`, интерфейс `IScriptEntry` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Возвращает текст, который соответствует тексту сообщения блока скрипта `IScriptEntry`, функции или блока скрипта.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Возвращает имя элемента, указывающее объект `IScriptEntry`.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Для записей, которые представляют один объект \(например, функция\), возвращают имя объекта.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Возвращает начальное положение и размер записи.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Сведения о типе возвращений для объекта функции `IScriptEntry`.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Возвращает текст, соответствующий блок скрипта `IScriptEntry` или исходный код, содержащийся в обработчике событий `IScriptScriptlet`.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Устанавливает текст, в тело блока скрипта `IScriptEntry` или сценария `IScriptScriptlet`.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Задает имя элемента, указывающее объект `IScriptEntry`.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Для записей, которые представляют один объект \(например, функция\) задает имя объекта.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Задает сведения о типе для объекта функции `IScriptEntry`.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Устанавливает текст, соответствующий блок скрипта `IScriptEntry` или исходный код, содержащийся в обработчике событий `IScriptScriptlet`.|  
  
## См. также  
 [Интерфейсы для создания активных скриптов](../../winscript/reference/active-script-authoring-interfaces.md)