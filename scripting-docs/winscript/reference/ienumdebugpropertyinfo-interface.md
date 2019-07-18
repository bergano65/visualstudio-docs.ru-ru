---
title: Интерфейс IEnumDebugPropertyInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugPropertyInfo interface
ms.assetid: c5eea4da-8414-408a-a8f6-6a9ca8745868
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 736bea847908e3c70d6caf2f8e41af38608f4f23
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963433"
---
# <a name="ienumdebugpropertyinfo-interface"></a>Интерфейс IEnumDebugPropertyInfo
Перечисляет `DebugPropertyInfo` структуры.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugPropertyInfo`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IEnumDebugPropertyInfo::Next](../../winscript/reference/ienumdebugpropertyinfo-next.md)|Извлекает указанное число `DebugPropertyInfo` структур в последовательности перечисления.|  
|[IEnumDebugPropertyInfo::Skip](../../winscript/reference/ienumdebugpropertyinfo-skip.md)|Пропускает заданное число `DebugPropertyInfo` структур в последовательности перечисления.|  
|[IEnumDebugPropertyInfo::Reset](../../winscript/reference/ienumdebugpropertyinfo-reset.md)|Сбрасывает последовательность перечисления в начало.|  
|[IEnumDebugPropertyInfo::Clone](../../winscript/reference/ienumdebugpropertyinfo-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[IEnumDebugPropertyInfo::GetCount](../../winscript/reference/ienumdebugpropertyinfo-getcount.md)|Получает число `DebugPropertyInfo` структур в перечислителе.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: dbgprop.h  
  
## <a name="see-also"></a>См. также  
 [Структура DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)