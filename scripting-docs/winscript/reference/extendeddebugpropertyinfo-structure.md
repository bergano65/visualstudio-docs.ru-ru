---
title: Структура ExtendedDebugPropertyInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ExtendedDebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fe0eef00d2bf064a8a002925f4ba5607d36f31c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955202"
---
# <a name="extendeddebugpropertyinfo-structure"></a>Структура ExtendedDebugPropertyInfo
Расширяет `DebugPropertyInfo` структуры с помощью дополнительных членов, характеризующее расширенного свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## <a name="members"></a>Участники  
 `dwValidFields`  
 Тип перечислимых данных, можно указать, какие поля инициализируются.  
  
 `bstrName`  
 Имя свойства в контексте.  
  
 `bstrType`  
 Тип свойства как форматируемой строки.  
  
 `bstrValue`  
 Значение свойства как отформатированную строку.  
  
 `bstrFullName`  
 Полное имя свойства.  
  
 `dwAttrib`  
 Перечисление, содержащее флаги для атрибутов свойства отладки.  
  
 `pDebugProp`  
 `IDebugProperty` Объект, соответствующий данному `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 Идентификатор диспетчера.  
  
 `nType`  
 Тип расширенного свойства.  
  
 `varValue`  
 Значение расширенного свойства, если он помещается в тип VARIANT.  
  
 `plbValue`  
 Байты фактических данных значения свойства.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty` Объект, соответствующий данному `ExtendedDebugPropertyInfo`.  
  
## <a name="see-also"></a>См. также  
 [Структура DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)   
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [Интерфейс IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)