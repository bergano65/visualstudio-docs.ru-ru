---
title: Интерфейс IDebugProperty | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugProperty interface
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e5e5274e8a3d1c81ce010afc3893b27510a0fad
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348364"
---
# <a name="idebugproperty-interface"></a>Интерфейс IDebugProperty
Используется для описания иерархической свойство сущности, для которого выполняется отладка, имеет имя, тип и значение. Чаще всего `IDebugProperty` используется для описания результата вычисления выражения, инструкции оценки или оценки регистра.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugProperty` интерфейс.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|Получить `DebugPropertyInfo` , описывающий это `IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|Получает расширенные сведения по свойству.|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|Задает значение свойства из строки.|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|Перечисляет члены коллекции свойства.|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|Возвращает родительский объект свойства.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: dbgprop.h