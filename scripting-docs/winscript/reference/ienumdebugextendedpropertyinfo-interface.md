---
title: Интерфейс IEnumDebugExtendedPropertyInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 2440daf99d9dbb69713d1895ffbfaa18965480a4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963487"
---
# <a name="ienumdebugextendedpropertyinfo-interface"></a>Интерфейс IEnumDebugExtendedPropertyInfo
Перечисляет `ExtendedDebugPropertyInfo` структуры.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugExtendedPropertyInfo`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IEnumDebugExtendedPropertyInfo::Clone](../../winscript/reference/ienumdebugextendedpropertyinfo-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[IEnumDebugExtendedPropertyInfo::GetCount](../../winscript/reference/ienumdebugextendedpropertyinfo-getcount.md)|Получает число `ExtendedDebugPropertyInfo` структур в перечислителе.|  
|[IEnumDebugExtendedPropertyInfo::Next](../../winscript/reference/ienumdebugextendedpropertyinfo-next.md)|Извлекает указанное число `ExtendedDebugPropertyInfo` структур в последовательности перечисления.|  
|[IEnumDebugExtendedPropertyInfo::Skip](../../winscript/reference/ienumdebugextendedpropertyinfo-skip.md)|Пропускает заданное число `ExtendedDebugPropertyInfo` структур в последовательности перечисления.|  
|[IEnumDebugExtendedPropertyInfo::Reset](../../winscript/reference/ienumdebugextendedpropertyinfo-reset.md)|Сбрасывает последовательность перечисления в начало.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: dbgprop.h  
  
## <a name="see-also"></a>См. также  
 [Структура ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)