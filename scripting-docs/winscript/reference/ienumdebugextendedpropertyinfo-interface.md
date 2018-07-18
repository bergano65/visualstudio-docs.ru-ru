---
title: Интерфейс IEnumDebugExtendedPropertyInfo | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo interface
ms.assetid: 316d5aa7-c949-48fc-89c1-239f00566cae
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c46815ff1fadd359e3200223dfe9041b6089ad3b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728174"
---
# <a name="ienumdebugextendedpropertyinfo-interface"></a>Интерфейс IEnumDebugExtendedPropertyInfo
Перечисляет `ExtendedDebugPropertyInfo` структуры.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugExtendedPropertyInfo`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IEnumDebugExtendedPropertyInfo::Clone](../../winscript/reference/ienumdebugextendedpropertyinfo-clone.md)|Создает перечислитель, с тем же состоянием, как у текущего перечислителя.|  
|[IEnumDebugExtendedPropertyInfo::GetCount](../../winscript/reference/ienumdebugextendedpropertyinfo-getcount.md)|Возвращает число `ExtendedDebugPropertyInfo` структуры в перечислителе.|  
|[IEnumDebugExtendedPropertyInfo::Next](../../winscript/reference/ienumdebugextendedpropertyinfo-next.md)|Извлекает указанное число `ExtendedDebugPropertyInfo` структуры в последовательности перечисления.|  
|[IEnumDebugExtendedPropertyInfo::Skip](../../winscript/reference/ienumdebugextendedpropertyinfo-skip.md)|Пропускает указанное число `ExtendedDebugPropertyInfo` структуры в последовательности перечисления.|  
|[IEnumDebugExtendedPropertyInfo::Reset](../../winscript/reference/ienumdebugextendedpropertyinfo-reset.md)|Сбрасывает последовательность перечисления в начало.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: dbgprop.h  
  
## <a name="see-also"></a>См. также  
 [Структура ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)