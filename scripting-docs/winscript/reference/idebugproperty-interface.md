---
title: Интерфейс IDebugProperty | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 963b11a4760fad8086822f13db129fae76467802
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979066"
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