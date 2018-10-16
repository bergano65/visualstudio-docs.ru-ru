---
title: Интерфейс IDebugProperty | Документы Microsoft
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
ms.openlocfilehash: 2888a6d781ecd501128545e483971a47859d9cda
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727064"
---
# <a name="idebugproperty-interface"></a>Интерфейс IDebugProperty
Используется для описания иерархической свойство сущности, для которого выполняется отладка, имеет имя, тип и значение. Чаще всего `IDebugProperty` используется для описания результат вычисления выражения, вычисление инструкции или evaluation регистра.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugProperty` интерфейса.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|Получить `DebugPropertyInfo` , описывающий это`IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|Возвращает расширенные сведения о свойстве.|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|Задает значение свойства из строки.|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|Перечисляет члены свойства.|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|Возвращает родительский объект свойства.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: dbgprop.h