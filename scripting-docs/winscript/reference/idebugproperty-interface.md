---
title: "Интерфейс IDebugProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugProperty — интерфейс"
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IDebugProperty
Используемый для описания любое свойство иерархическое отлаживаемый сущности, у которой есть имя, тип и значение.  Чаще всего `IDebugProperty` используется для описания результат оценки выражений, вычислений выписки или оценки регистра.  
  
## Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы интерфейса `IDebugProperty`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|Получение `DebugPropertyInfo`, которое описывает это `IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|Получает расширенные сведения о свойстве.|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|Устанавливает значения свойства из строки.|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|Перечисляет членов свойства.|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|Возвращает родительский объект свойства.|  
  
## Требования  
 Заголовок: dbgprop.h